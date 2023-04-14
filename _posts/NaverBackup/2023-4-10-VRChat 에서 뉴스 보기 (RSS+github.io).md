---
title: "VRChat 에서 뉴스 보기 (RSS+github.io)"
categories:
 - personalproject
---
#VRChat 에서 뉴스 보기 (RSS+github.io) : 네이버 블로그








> 
> 들어가며
> 
> 
> VRChat 패치 소식: 웹에서 텍스트 가져오기 기능 추가됨!
> 
> 
> 









* [VRChat에서는 Udon이라는 언어를 VM에서 실행할 수 있습니다.](https://docs.vrchat.com/docs/what-is-udon) 이 Udon을 확장한 [UdonSharp](https://udonsharp.docs.vrchat.com/)는 C# 문법을 사용하여 VRChat 내부에서 게임이나 특정한 기능을 동작시킵니다. 다만, Udon에서 지원하지 않는 기능 중에는 대표적으로 웹과의 통신이 있습니다.

​

* 따라서 유저들은 외부와 데이터 전송을 위해 디버그 로그를 통해 월드의 데이터를 외부로 빼거나, [웹 비디오 플레이어를 이용하여 데이터를 외부에서 받는 등](https://feralresearch.org/lab/api-calls-from-inside-vrc/) 다양한 꼼수를 개발해왔습니다.

​

* 약 반년 전, [아바타와 로컬 PC 간 통신이 가능한 OSC 프로토콜](https://docs.vrchat.com/docs/osc-overview)이 지원되면서 상황이 약간 개선되었습니다. 하지만 이는 월드용이 아닌 아바타용 프로토콜이기 때문에 월드 측면에서는 여전히 진전이 없었습니다.

​

* 그러던 중 2023년 3월 패치에서 [웹에서 텍스트를 가져오는](https://docs.vrchat.com/docs/string-loading) 기능과 [이미지를 가져오는](https://docs.vrchat.com/docs/image-loading) 기능을 추가했습니다.

​

​

​





 



> 
> 아이디어
> 
> 
> 무엇을 할까?
> 
> 
> 









VRChat에서 웹과 통신이 가능해지면서 많은 가능성이 열렸습니다. 예를 들어, 새로운 RPG 월드에서 SQL 데이터 테이블과 연동하여 플레이어 정보를 저장할 수 있고, 카지노 월드에서는 자신의 소지금 외부에 저장할 수 있습니다. 또한 실시간으로 주식 정보도 가져올 수 있겠네요.

​

필자는 VRChat에서 무엇을 가져올까? 고민고민하다 뉴스를 가져오는 기능을 추가하기로 결정했습니다. 이를 위해 해야 할 과정을 생각해보자면 다음과 같습니다:

​

1. 다양한 언론사의 뉴스를 가공해서 웹에 올리기
2. 웹에서 텍스트를 받아 구문분석(parsing)하기

​

​

​





 



> 
> StringLoading 맛보기
> 
> 
> 이젠 이미지도 불러올수 있다구
> 
> 
> 









이번에 추가된 [StringLoading 문서](https://docs.vrchat.com/docs/string-loading)를 보면, 

* 5초에 하나의 문자열(링크)만 다운로드 가능
* 한 문자열은 최대 100MB
* 대기열은 최대 1000개
* 신뢰하는 URL은 (\*.github.io, pastebin.com,gist.githubusercontent.com)이다. 꼭 이 도메인이 아니더라도 유저가 'Allow Untrusted URLs’옵션을 키면, 다른 도메인도 가능하다.

​

추가된 노드로는 

​

* 이벤트


	+ OnStringLoadSuccess
	+ OnStringLoadError
* VRCStringDownloader.LoadUrl(Url , UdonBehaviour)


	+ String을 가져오는 노드이다
	+ Url은 String을 가져올 링크, UdonBehaviour는 링크를 가져왔을 때 이벤트(OnStringLoad)가 실행될 대상이다
* IVRCStringDownload : String을 가져온 Result입니다


	+ Error : Load에 대한 오륲 메시지를 가져옵니다
	+ ErrorCode : Load에 대한 HTTP오류 코드를 가져옵니다
	+ Response : 다운로드된 문자열
	+ UdonBehaviour : Load이벤트를 전송할 UdonBehaviour

​

주의할 점은 **UdonSharp**를 사용해서 코드를 작성할 때 

VRC.SDK3.StringLoading.VRCStringDownloader.LoadUrl(Url)을 해도 컴파일 오류가 나지는 않지만, 실행 중 이벤트를 보낼 타겟이 null로 되어 있어 오류가 납니다.

​

그렇기에 VRC.SDK3.StringLoading.VRCStringDownloader.LoadUrl(Url,**GetComponent<UdonBehaviour>()**)로 이벤트를 받을 대상을 지정해줘야 합니다.

​

​

​

아래는 링크를 로드해 디버그 로그로 띄우는 코드입니다

UdonGraph





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/0.png)](#)









```
application/vnd.unity.graphview.elements AM2W227bRhCGX8XYay2x54MB38RKCyFBU9ixchEYwp4osKGWBQ9ODSdP1os+Ul+hI1FyGkkohMQuAupCXO4uZ/6Z/+P+/edfD+jO1UNC5+8fUDnU9S9uBTdo7trK+Tot5leX19NXL1yX4N9NW6MJGqoIMwQP0QhDcEkFwSJ4ji2hFCvDeLJMCmsJTP696aq+ajI6f0B/oHPMrSiU5pZapbXmQkzQPQxTTQpBORGEKko5M58nKDcx3cymHcSGYKcvv9sJKuvm4/bZ7Thzvk6j2+Qx5Kq/f+N/S6Gfj8k9oCp3vcshzabonMDmXd9Webl9jNDnybcsu77v+rQqrjeDk7NVF5q2rvzkbJ7aDpK+EAVZX5Ozy6HuhzZd5DT0rasnZ78Ovq7Cq3T/tvmQ8oXX2skgFbVcJGLsp3fJv67yh+8L7EXT1Mnlp43sbQuv+PHC+snV3XfG9Rx1zE2GqG7Xcf3LXi/vUu4Xs9yn1oX+0VOJyFIkobE3kmPBBMWeOI2jjYwTuDzhRzzFwDzUSqWNpsRyLbeeUrSQX/voa+egQGFDmkosnEtYyKSxcyri4KIJxjtuVIn2/bWfy0gIPor3unFxLSyMbe6nzcdcw1hqi8Vi/RAQsjiAynrgJjb5slmtmryRpXQhdbP14EarqxRSdZfaxWKs1bwBwXaynZTGgWzMFpQYYBGxUsN6pnYo0oWxlFkF6zQ1Wu2xyBvQOZYl1oxHIB/gz8cUcDQslJEkxoj5RA5BhQ6k/B9RddiDP6d+scP8o5Sn5HasAxkrtIJ+F1pLbonio5ZKFwxYz6UWDJSU+1R/epI/o5VP+uI9VXVu1nu8zMsqp2nyw3Jjn+Wu/cfNj5rBKKp4qQN2sdyYwWBDpcXwYYUu91LGkh0xwxYhwkC6XNrtZ9luqqoEk9pQtl8+ZWhMSXgQJEKzeOaxKwnFwYeSMCoNUe6YEX4oG4wofpO/8Ot6CMCe7lFRqmRMKkpcptJgoRIFvNgSc+2dVtKlYOMxT3BTKDjRCM2BIVaOluB2c/zhwnIlGZx//hPQJxXzWwA9OyA0NNgSiHCVOvDFrrPGKY9KnFLwQyWMKgjkShVRQkhORyG2mOWUKiEl0fsnvlNUh+Z6js66hesf
```





 



​

​

​

​

​

UdonSharp





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/1.png)](#)









```
using System;
using UdonSharp;
using UnityEngine;
using VRC.SDK3.StringLoading;
using VRC.SDKBase;
using VRC.Udon;

public class Test : UdonSharpBehaviour
{

 VRCUrl adf= new VRCUrl("https://feralresearch.org/lab/api-calls-from-inside-vrc/");
 public override void Interact()
 {
 VRC.SDK3.StringLoading.VRCStringDownloader.LoadUrl(adf,gameObject.GetComponent());
 }

 public override void OnStringLoadSuccess(IVRCStringDownload result)
 {
 Debug.Log(result.Result);
 }

 
}
```





 



​

​

​

​

​





 



> 
> 자바스크립트로 RSS불러오기
> 
> 
> 바보같은 결과가 나왔다!
> 
> 
> 









우선 깃허브 리포지토리를 하나 만들고, Github Pages를 설정합니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/2.png)](#)








​

그리고서 rss를 가져오는 자바스크립트를 html로 커밋합니다





 




```




RSS Feed Example with Proxy Server


RSS Feed Example with Proxy Server
==================================




 // RSS 피드 URL
 const feedUrl = "https://www.yonhapnewstv.co.kr/browse/feed/";

 // Proxy 서버 URL.
 const proxyUrl = "https://cors-anywhere.herokuapp.com/";

 // RSS 피드를 가져옵니다.
 fetch(proxyUrl + feedUrl)
 .then(response => response.text())
 .then(data => {
 // RSS 피드의 제목을 가져옵니다.
 const parser = new DOMParser();
 const xmlDoc = parser.parseFromString(data, "text/xml");
 const title = xmlDoc.getElementsByTagName("title")[0].childNodes[0].nodeValue;

 // RSS 피드의 아이템을 가져와서 HTML에 적용합니다.
 const items = xmlDoc.getElementsByTagName("item");
 let html = "<h2>" + title + "</h2><ul>";
 for (let i = 0; i < items.length; i++) {
 const itemTitle = items[i].getElementsByTagName("title")[0].childNodes[0].nodeValue;
 const itemLink = items[i].getElementsByTagName("link")[0].childNodes[0].nodeValue;
 html += "<li><a href='" + itemLink + "'>" + itemTitle + "</a></li>";
 }
 html += "</ul>";

 // HTML에 RSS 피드를 적용합니다.
 document.getElementById("feed").innerHTML = html;
 })
 .catch(error => console.log(error));
 


```





 



​

RSS를 그냥 가져오니 CORS에 막하는 에러가 났기 때문에 [proxy](https://github.com/Rob--W/cors-anywhere)를 제공하는 서비스를 경유했습니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/3.png)](#)









```
Access to fetch at 'https://www.yonhapnewstv.co.kr/browse/feed/' from origin 'null' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource. If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled.
```





 



​

CORS(Cross-Origin Resource Sharing)는 웹 브라우저에서 보안 상의 이유로 다른 도메인의 리소스에 직접 액세스하는 것을 제한하는 정책입니다.

​

​

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/4.png)](#)








자바스크립트로 가져온 RSS

​

이 링크를 유니티에서 StringLoad 해보았지만...

​

​

​

​

​

예상치도 못한 결과

​

유니티에서 string을 가져오니, 자바스크립트가 실행 된 결과가 아니라, 자바스크립트 코드 자체를 가져왔다 ㅋㅋ





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/5.png)](#)








당연히 페이지 자체를 가져오니 자바스크립트를 가져오는구나... ㅋㅋ

쓸데없이 html 난독화를 찾아본건 덤

​

​

​

뉴스를 수정하려면 계속 커밋을 해야 하는데, 컴퓨터를 항상 킬 수는 없으니, 클라우드 컴퓨팅을 이용하기로 했다.

​

옛날에 만들어놓은 계정이 있으나, 현재 프리티어 혜택이 적용이 안되는 것으로 알고있다

그렇기에 계정을 새로 판 후 VM을 생성했다.





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/6.png)](#)








[무료로 사용이 가능한 조건](https://cloud.google.com/free/docs/free-cloud-features?hl=ko#compute):

e2-micro

지역 제한

30GB/월 표준 디스크

​

​

​

​

​

​

​

​

​





 



> 
> 깃허브 리포지토리 SSH 연결
> 
> 
> 우분투에서 SSH키 연결하기
> 
> 
> 









깃허브 리포지토리는 SSH(Secure Shell)사용이 가능하기 때문에, 키를 등록해놓으면 따로 아이디와 패스워드를 이용해 연결하지 않아도 된다.

​

연결은 클라이언트에서 키(공개키)를 생성후, 깃허브 리포지토리에서 등록 하면 된다.

​

우분투에서 githubSSH를 연결하는 방법은

​

1. 클라이언트에서 SSH키를 생성한다

ssh-keygen -t rsa -b 4096 -C "github@example.com"

​

ssh-keygen으로 SSH키를 생성 할 수 있다.

​

2. SSH 키를 복사하기

cat ~/.ssh/id\_rsa.pub

​

3. GIthub 리포지토리에서 SSH 키 생성하기

​

세팅의 Deploy Key를 등록하면 된다.





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/7.png)](#)








​

git pull로 원하는 디렉토리에 리포지토리를 받는다. 파일을 수정하고 커밋을 한 후

​

Username for '[https://github.com':](https://github.com%27:) 을 입력하라고 나올때는 깃허브 연결이 SSH가 아닌 HTTPS로 되어서 그렇다. 

​

git remote -v로 입력했을때





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/8.png)](#)








이렇게 https:로 연결된다면,





 




```
git remote set-url origin git@github.com:사용자이름/리포지토리이름.git
```





 



을 입력해서 SSH연결로 바꿔줘야 한다.

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/9.png)](#)








바뀐 저장소 연결

​

​

​

여기서 필자는 서버에서의 커밋 기록이 Github Contributors에 남기고 싶지 않아서 부계정을 이용했다.

 깃허브 리포지토리를 부계정으로 옮긴 뒤 SSH키를 등록한 후 다시 본계정으로 소유권을 옮기면 SSH로 커밋을 해도 키를 만든 부계정 이름으로 커밋된다.

​

하루도 빠짐없이 48개를 커밋하는 사람이 있다고 하면 무섭지 않은가...

​

​

​

​

​

​





 



> 
> RSS를 받아서 언론사.HTML로 저장한 후 커밋하는 코드 작성
> 
> 
> 









다음은 코드 작성이다.

​

기능은 RSS를 받아 언론사이름.HTML로 저장하는 기능이다.

​

파이썬은 라이브러리들이 편하게 되어있기에 RSS를 가져와주는 feedparser를 사용했다.

​

Feedparser는 RSS뿐만이 아니라 Atom, RDF같은 웹 피드 형식을 파싱 가능하다.

​

Feedparser에는 title, link, published, summary가 포함된다.

​

필자가 쓸 것은 title과 기사의 내용.

​

기사의 내용은 content, summary, description 등이 있는데, 이는 언론사 RSS 피드의 형식에 따라 다르다. 그렇기에 세개를 모두 받아온 뒤 가장 긴 내용을 사용하기로 했다.

​

내용에서는 html태그와 쓸모 없는 괄호들도 포함되기에 길이를 비교하기 전 꼭 제거해야 한다.

​

그리고 기사에는 잘 쓰이지 않는 특수문자를 이용하여 ^은 테마, \_로는 각 기사들을 구분했다. 특수문자로 나눈 이유는 유니티에서 string을 사용하는 특성상 가비지가 쌓이기 때문에, 특히 VR을 사용하는 환경에서는 영향이 있다. 그렇기에 char split으로 나눌 수 있는 특수문자를 사용했다.

​

또 <body>의 첫줄은 테마\_테마\_테마\_ 처럼 \_바로 구분했다. 그럼 나중에 테마의 수와 종류를 바로 받을 수 있겠지

​

그리고서 while과 sleep으로 일정 시간마다 반복되게끔 해두었다.





 




```
import feedparser
import subprocess
import os
import time
from bs4 import BeautifulSoup
import time

def remove\_parenthesis(string):
 # 주어진 문자열에서 괄호로 시작하는 부분을 찾아 삭제
 while True:
 start\_index = string.find("{")
 end\_index = string.find("}")
 if(end\_index-start\_index<1000):
 if start\_index != -1 and end\_index != -1:
 string = string[:start\_index] + string[end\_index+1:]
 else:
 break
 # 삭제된 문자열 반환
 return string


def remove\_p\_and\_img\_tags(html\_text):
 html\_text = str(html\_text)
 soup = BeautifulSoup(html\_text, 'html.parser')
 for tag in soup(['p', 'img']):
 tag.decompose()
 return remove\_parenthesis(str(soup))








# ssh-agent 실행
ssh\_agent = subprocess.Popen(['ssh-agent', '-s'], stdout=subprocess.PIPE)
# ssh-add 실행
subprocess.call('ssh-add ~/.ssh/id\_rsa', shell=True)
# RSS 피드 URL 설정

rss\_url = "http://www.yonhapnewstv.co.kr/browse/feed/"
# feedparser로 RSS 뉴스 기사 파싱
feed = feedparser.parse(rss\_url)

# 저장할 파일 경로와 파일명 설정
base\_path = "/home/dls32208/Documents/VRChatKoreaNews"
file\_name = "news.html"


rss\_urls = {
 '조선일보': {
 '전체기사': 'https://www.chosun.com/arc/outboundfeeds/rss/?outputType=xml',
 '정치': 'https://www.chosun.com/arc/outboundfeeds/rss/category/politics/?outputType=xml',
 '경제': 'https://www.chosun.com/arc/outboundfeeds/rss/category/economy/?outputType=xml',
 '사회': 'https://www.chosun.com/arc/outboundfeeds/rss/category/national/?outputType=xml',
 '국제': 'https://www.chosun.com/arc/outboundfeeds/rss/category/international/?outputType=xml',
 '문화라이프': 'https://www.chosun.com/arc/outboundfeeds/rss/category/culture-life/?outputType=xml',
 '오피니언': 'https://www.chosun.com/arc/outboundfeeds/rss/category/opinion/?outputType=xml',
 '스포츠': 'https://www.chosun.com/arc/outboundfeeds/rss/category/sports/?outputType=xml',
 '연예': 'https://www.chosun.com/arc/outboundfeeds/rss/category/entertainments/?outputType=xml'
 },
 '동아일보': {
 '전체기사': 'https://rss.donga.com/total.xml',
 '정치': 'https://rss.donga.com/politics.xml',
 '사회': 'https://rss.donga.com/national.xml',
 '경제': 'https://rss.donga.com/economy.xml',
 '국제': 'https://rss.donga.com/international.xml',
 '사설칼럼': 'https://rss.donga.com/editorials.xml',
 '의학과학': 'https://rss.donga.com/science.xml',
 '문화연예': 'https://rss.donga.com/culture.xml',
 '스포츠': 'https://rss.donga.com/sports.xml',
 '사람속으로': 'https://rss.donga.com/inmul.xml',
 '건강': 'https://rss.donga.com/health.xml',
 '레져': 'https://rss.donga.com/leisure.xml',
 '도서': 'https://rss.donga.com/book.xml',
 '공연': 'https://rss.donga.com/show.xml',
 '여성': 'https://rss.donga.com/woman.xml',
 '여행': 'https://rss.donga.com/travel.xml',
 '생활정보': 'https://rss.donga.com/lifeinfo.xml',
 '스포츠': 'https://rss.donga.com/sportsdonga/sports.xml',
 '야구MLB': 'https://rss.donga.com/sportsdonga/baseball.xml',
 '축구': 'https://rss.donga.com/sportsdonga/soccer.xml',
 '골프': 'https://rss.donga.com/sportsdonga/golf.xml',
 '일반': 'https://rss.donga.com/sportsdonga/sports\_general.xml',
 'e스포츠': 'https://rss.donga.com/sportsdonga/sports\_game.xml',
 '엔터테인먼트': 'https://rss.donga.com/sportsdonga/entertainment.xml',
 },
 '매일경제': {
 '헤드라인': 'https://www.mk.co.kr/rss/30000001/',
 '전체뉴스': 'https://www.mk.co.kr/rss/40300001/',
 '경제': 'https://www.mk.co.kr/rss/30100041/',
 '정치': 'https://www.mk.co.kr/rss/30200030/',
 '사회': 'https://www.mk.co.kr/rss/50400012/',
 '국제': 'https://www.mk.co.kr/rss/30300018/',
 '기업경영': 'https://www.mk.co.kr/rss/50100032/',
 '증권': 'https://www.mk.co.kr/rss/50200011/',
 '부동산': 'https://www.mk.co.kr/rss/50300009/',
 '문화연예': 'https://www.mk.co.kr/rss/30000023/',
 '스포츠': 'https://www.mk.co.kr/rss/71000001/',
 '게임': 'https://www.mk.co.kr/rss/50700001/',
 'MBA': 'https://www.mk.co.kr/rss/40200124/',
 '머니앤리치스': 'https://www.mk.co.kr/rss/40200003/',
 'English': 'https://www.mk.co.kr/rss/30800011/',
 '이코노미': 'https://www.mk.co.kr/rss/50000001/',
 '시티라이프': 'https://www.mk.co.kr/rss/60000007/'
 }
}
```





 




```
while True:
 for press in rss\_urls:
 file\_name = f"{press}.html"
 file\_path = os.path.join(base\_path, file\_name)
 press\_html = ""
 titleList=""
 for category in rss\_urls[press]:
 rss\_url = rss\_urls[press][category]
 # feedparser로 RSS 뉴스 기사 파싱
 feed = feedparser.parse(rss\_url)
 # 기사 정보를 HTML 코드로 변환하여 press\_html에 추가
 titleList=titleList+category+"\_"
 for entry in feed.entries:
 temp = f"\_{entry.title}\n"
 try:
 if len(remove\_p\_and\_img\_tags(entry.content[0])) > len(remove\_p\_and\_img\_tags(entry.description)) and len(remove\_p\_and\_img\_tags(entry.content[0])) > len(remove\_p\_and\_img\_tags(entry.summary)):
 if len(remove\_p\_and\_img\_tags(entry.content[0])) <2:
 continue
 temp += f"{remove\_p\_and\_img\_tags(entry.content[0])}\n\n"
 else:
 if len(remove\_p\_and\_img\_tags(entry.summary)) < 2:
 continue
 temp += f"{remove\_p\_and\_img\_tags(entry.summary)}\n\n"
 except AttributeError:
 if len(remove\_p\_and\_img\_tags(entry.description)) < 2:
 continue
 temp +=f"{remove\_p\_and\_img\_tags(entry.description)}\n\n"
 press\_html = press\_html+temp
 press\_html +="^"; 

 press\_html=titleList+'\n'+press\_html

 # HTML 파일 생성
 with open(file\_path, "w") as f:
 f.write("\n\nNews\n\n\n")
 f.write(press\_html)
 f.write("\n")

 # 각 언론사별로 commit 및 push
 subprocess.call(f"git add {file\_path}", cwd=base\_path, shell=True)
 subprocess.call(f"git commit -m 'Update news' && git push", cwd=base\_path, shell=True)

 # 1분 대기
 time.sleep(1800)
```





 



sleep()을 쓰지 않고 cron에 스케줄을 등록하는 방법도 있다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/10.png)](#)








​

​

​





 



> 
> 실행 및 파일 확인
> 
> 
> 마무리하며
> 
> 
> 









구글 클라우드 컴퓨터는 SSH 세션 연결이 끝나면 실행 중인 프로세스들도 종료하므로 백그라운드에서 실행해야 한다. 그렇기에 nohup명령어(유닉스 백그라운드 실행)로 실행했다.

​

nohup python3 my\_script.py > ~/logs/my\_script.log &

>은 재지정자로, 백그라운드에서 실행하면 로그가 저장되는데, 같이 저장되면 커밋에서 꼬이기 때문에 다른 디렉토리로 재지정한다.

​

​

[동아일보](https://rage147-owo.github.io/VRChatKoreaNews/%EB%8F%99%EC%95%84%EC%9D%BC%EB%B3%B4.html)

[매일경제](https://rage147-owo.github.io/VRChatKoreaNews/%EB%A7%A4%EC%9D%BC%EA%B2%BD%EC%A0%9C.html)

[조선일보](https://rage147-owo.github.io/VRChatKoreaNews/%EC%A1%B0%EC%84%A0%EC%9D%BC%EB%B3%B4.html)

HTML로 github.io에서 잘 작동하는것을 볼 수 있다.

​

​

​

<https://github.com/rage147-OwO/VRChatKoreaNews>

쓸데없는 커밋이 많으니 깃허브에게 미안하기도 하다.

커밋 아카이브를 끌 수 있던데, 그걸 끄면 커밋 기록을 사용하지 않을 수 있을지는 모르겠다.

​

시간이 나면 네이버 블로그를 RSS로 받아서 깃허브에 자동으로 연동시켜 둘 것이기 때문에 요 코드는 나중에도 요긴한게 쓰일 것 같다.

​

​

다음편은 유니티 클라이언트에서의 개발이다.





 

