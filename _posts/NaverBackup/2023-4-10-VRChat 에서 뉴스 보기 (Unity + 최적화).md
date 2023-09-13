---
title: "VRChat 에서 뉴스 보기 (Unity + 최적화)"
categories:
 - personalproject
---








[VRChat 에서 뉴스 보기 (RSS+github.io)와 이어집니다](https://blog.naver.com/dls32208/223070716515)





 



> 
> 들어가며
> 
> 
> 









전 포스팅에서는 RSS를 받아와 github.io에 자동으로 커밋하게끔 구축해두었다.

[동아일보](https://rage147-owo.github.io/VRChatKoreaNews/%EB%8F%99%EC%95%84%EC%9D%BC%EB%B3%B4.html)

[매일경제](https://rage147-owo.github.io/VRChatKoreaNews/%EB%A7%A4%EC%9D%BC%EA%B2%BD%EC%A0%9C.html)

[조선일보](https://rage147-owo.github.io/VRChatKoreaNews/%EC%A1%B0%EC%84%A0%EC%9D%BC%EB%B3%B4.html)

​

HTML은 다음과 같다





 




```


테마0\_테마1\_테마2\_테마3\_
테마0\_기사0
기사1
기사2
기사3
....
^테마1\_기사0
기사1
기사2
....
```





 



Unity에서 필요한 기능은

* 언론사, 테마에 따라 변경되는 UI
* 한 면에 표시되는 기사의 수를 조절

를 목표로 했다.

​

​





 



> 
> Unity UI
> 
> 
> 버튼과 스크롤 뷰를 활용
> 
> 
> 









우선적으로 생각해야 할 것은, 언론사의 수, 테마의 수만큼 버튼을 생성/삭제 하는것이다. 인스턴스화와 디스트로이로 생성/삭제가 가능하지만, 조금 귀찮더라도 셋 액티브로 해결하기로 했다.





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (Unity + 최적화)/0.png)](#)








Unity UI의 든든 국밥같은 친구, 스크롤뷰의 LayoutGroup과 ContentSizeFilter를 이용했다.

​

LayoutGroup은 자식 오브젝트를 자동으로 정렬해주는 기능이다. 수직 또는 수평으로 자식 오브젝트를 나열하고, 간격을 설정할 수 있다. 

​

ContentSizeFilter는 UI 요소의 크기를 자동으로 조절하는 기능이다. 이 컴포넌트를 사용하면 부모 오브젝트의 크기에 맞게 UI 요소의 크기를 조절할 수 있다. 예를 들면, 부모 오브젝트의 크기가 변경되면 자식 UI 요소의 크기도 자동으로 조절된다.

​

버튼은 자동으로 왼쪽부터 채워지니, 모두 끈 후 필요한 수만큼 키면 되는것이다.

​

스크롤뷰의 콘텐츠에 버튼을 넣으면 레이캐스트가 겹쳐, 버튼의 클릭이 되지 않고 스크롤뷰로 가는 버그가 있는데, Event Trigger컴포넌트를 넣어 우선 순위를 올려주면 된다. 

​

그 밖에는... 음..

​

VRChat한정으로 버튼과 상호작용을 하려면 레이아웃을 디폴트로, 캔버스에 VRC UI Shape 컴포넌트를 넣어줘야 한다.

​

그 밖에는 WASD키를 누르면 UI가 움직이니 Navigation을 꺼야 한다 정도?





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (Unity + 최적화)/1.png)](#)








필요한 것만 넣어둔 컨트롤 패널





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (Unity + 최적화)/2.png)](#)








컨트롤 패널만 있으면 심심하니 VR로 들고 다닐 수 있는 미니패널 하나

​

사실 구현보다 배경 텍스쳐 고르는게 더 힘들었다 ㅋㅋ

​

이과의 감성이란...

​

어짜피 뉴스 기능이 필요한 사람은 받은 다음에 꾸며서 쓰지 않을까....

기능에 집중하자

​

​





 



> 
> HTML 파싱 코드
> 
> 
> 파싱 라이브러리를 사용할 수 없어
> 
> 
> 









이젠 HTML을 불러와서 기사를 잘라야 한다

생각해야 할 것은

* 기능


	+ 사용자가 HTML로드중일 때 조작을 못하게 예외처리
	+ 사용자가 한 페이지의 기사 수를 조절 할 수 있게 만들기
* 최적화


	+ VR유저가 많은 많큼, 많은 양의 String을 처리하기에 가비지가 쌓이기 쉽다. Substring을 최소화하고 최대한 인덱스로 접근하자.
	+ 한 페이지를 표시할때도 최대한 인덱스로 접근하자
	+ 미리 뉴스를 가져오기보다는 필요할 때만 가져오게 하자
	+ 중복되는 기능을 묶고 메소드로 만들자





 




```
using System;
using System.Linq;
using System.Text;
using UdonSharp;
using UnityEngine;
using UnityEngine.UI;
using VRC.SDK3.StringLoading;
using VRC.SDKBase;
using VRC.Udon;

public class KoreaNews : UdonSharpBehaviour
{
 private VRCUrl[] pressUrls = new VRCUrl[]
 {
 new VRCUrl("https://rage147-owo.github.io/VRChatKoreaNews/%EB%8F%99%EC%95%84%EC%9D%BC%EB%B3%B4.html"),
 new VRCUrl("https://rage147-owo.github.io/VRChatKoreaNews/%EB%A7%A4%EC%9D%BC%EA%B2%BD%EC%A0%9C.html"),
 new VRCUrl("https://rage147-owo.github.io/VRChatKoreaNews/%EC%A1%B0%EC%84%A0%EC%9D%BC%EB%B3%B4.html")
 };

 private string[] pressNames = new string[]
 {
 "동아일보",
 "매일경제",
 "조선일보"
 };
 [SerializeField] private Transform pressButtonParent;
 [SerializeField] private Transform themaButtonParent;
 [SerializeField] private Text newsText;
 [SerializeField] private Text PickUpText;
 [SerializeField] private int pageSize = 4;
 [SerializeField] private Text pageText;
 [SerializeField] private Text StatusText;

 private string \_news;
 private string \_articles;
 private string[] \_thema;
 private int \_currentPage = 1;
 private int \_currentThema = 0;
 private int \_maxPage;
 private int[] \_themaIndexes;
 private int[] \_pageIndexes;
 bool IsReady = false;

 private void Start()
 {
 Debug.Log("pressNameLength" + pressNames.Length);
 CreateButtons(pressButtonParent, pressNames.Length, pressNames);
 themaButtonParent.gameObject.SetActive(false);
 SetStatusText("IsReady");
 }

 private void SetStatusText(string \_\_text)
 {
 StatusText.text = \_\_text;
 }

 public override void OnStringLoadSuccess(IVRCStringDownload result)
 {
 \_news = result.Result.Substring(49, result.Result.Length - 16 - 49);
 int firstNewlineIndex = \_news.IndexOf('\n');
 \_thema = \_news.Substring(0, firstNewlineIndex).TrimEnd('\_').Split('\_');
 \_news = \_news.Remove(0, firstNewlineIndex + 1);
 CreateButtons(themaButtonParent, \_thema.Length, \_thema);
 SetThemaIndexes();
 SetStatusText("Last Update: " + DateTime.Now.ToString("yyyy-MM-dd HH:mm:ss"));
 themaButtonParent.gameObject.SetActive(true);
 }

 private void CreateButtons(Transform parent, int buttonCount, string[] buttonTexts)
 {
 Debug.Log("CreateButtons: " + buttonCount + " called");

 Text[] textComponents = parent.GetComponentsInChildren();

 for (int i = 0; i < textComponents.Length; i++)
 {
 if (i < buttonCount)
 {
 textComponents[i].transform.parent.gameObject.SetActive(true);
 textComponents[i].text = buttonTexts[i];
 }
 else
 {
 textComponents[i].transform.parent.gameObject.SetActive(false);
 }
 }
 }

 private void ShowPage(int page, int themeIndex)
 {

 pageText.text = page + "/" + \_maxPage;
 if (page == 1)
 {
 newsText.text = \_articles.Substring(0, \_pageIndexes[1]);
 PickUpText.text = newsText.text;
 }
 else if (page == \_maxPage)
 {
 Debug.Log("LastPage");
 newsText.text = \_articles.Substring(\_pageIndexes[\_pageIndexes.Length-1], \_articles.Length - \_pageIndexes[\_pageIndexes.Length - 1]);
 PickUpText.text = newsText.text;
 }
 else
 {
 newsText.text = \_articles.Substring(\_pageIndexes[page - 1], \_pageIndexes[page] - \_pageIndexes[page - 1]);
 PickUpText.text = newsText.text;
 }
 }

 private string GetArticlesForTheme(int themeIndex)
 {
 if (themeIndex == 0)
 {
 return \_news.Substring(0, \_themaIndexes[0]);
 }

 if (themeIndex == \_thema.Length - 1)
 {
 return \_news.Substring(\_themaIndexes[themeIndex - 1], \_news.Length - \_themaIndexes[themeIndex - 1]);
 }

 return \_news.Substring(\_themaIndexes[themeIndex - 1],
 \_themaIndexes[themeIndex] - \_themaIndexes[themeIndex - 1]);
 }
 
 public void NextPage()
 {
 if(IsReady== false)
 return;
 Debug.Log("NextPage");
 if (\_currentPage < \_maxPage)
 {
 \_currentPage++;
 ShowPage(\_currentPage, \_currentThema);
 }
 }

 public void PrePage()
 {
 if(IsReady== false)
 return;
 Debug.Log("PrePage");
 if (\_currentPage > 1)
 {
 \_currentPage--;
 ShowPage(\_currentPage, \_currentThema);
 }
 }
```





 




```
private void SetPageIndexes(int themeIndex)
 {
 \_articles = GetArticlesForTheme(themeIndex);
 int count = 0;
 for (int i = 0; i < \_articles.Length; i++)
 {
 if (\_articles[i] == '\_')
 {
 Debug.Log(\_articles);
 count++;
 }
 }
 \_maxPage = count / pageSize;

 if (count < pageSize\*2)
 {
 \_maxPage = 2;
 }
 \_pageIndexes = new int[\_maxPage];

 int lastIndex = 0;
 int temp = 0;
 
 
 for (int i = 0; i < count; i++)
 {
 if(\_pageIndexes.Length == temp)
 {
 Debug.Log(temp);
 for(int j=0;j<\_pageIndexes.Length;j++)
 {
 Debug.Log("PageIndexes: " + j + " " + \_pageIndexes[j]);
 }
 break;
 }
 int currentIndex = \_articles.IndexOf('\_', lastIndex);
 lastIndex = currentIndex + 1;

 if (i % pageSize == 0)
 {
 \_pageIndexes[temp] = currentIndex;
 temp++;
 }
 }
 IsReady= true;
 }

 private void SetThemaIndexes()
 {
 int themeCount = \_thema.Length;
 \_themaIndexes = new int[themeCount - 1];

 int lastIndex = 0;

 for (int i = 0; i < themeCount - 1; i++)
 {
 int currentIndex = \_news.IndexOf('^', lastIndex);
 \_themaIndexes[i] = currentIndex;
 lastIndex = currentIndex + 1;
 }
 }

 public void ThemaButtonClicked(int themaIndex)
 {
 Debug.Log("ThemaButtonCkick : " + themaIndex + "");
 \_currentThema = themaIndex;
 SetPageIndexes(themaIndex);
 \_currentPage = 1;
 ShowPage(1, themaIndex);
 }

 public void Press(int pressIndex)
 {
 Debug.Log("PressButton : " + pressIndex + "");

 VRC.SDK3.StringLoading.VRCStringDownloader.LoadUrl(pressUrls[pressIndex], GetComponent());
 themaButtonParent.gameObject.SetActive(false);
 SetStatusText("Loading...");
 }

 public void Thema0()
 {
 ThemaButtonClicked(0);
 }

 public void Thema1() => ThemaButtonClicked(1);
 public void Thema2() => ThemaButtonClicked(2);
 public void Thema3() => ThemaButtonClicked(3);
 public void Thema4() => ThemaButtonClicked(4);
 public void Thema5() => ThemaButtonClicked(5);
 public void Thema6() => ThemaButtonClicked(6);
 public void Thema7() => ThemaButtonClicked(7);
 public void Thema8() => ThemaButtonClicked(8);
 public void Thema9() => ThemaButtonClicked(9);
 public void Thema10() => ThemaButtonClicked(10);
 public void Thema11() => ThemaButtonClicked(11);
 public void Thema12() => ThemaButtonClicked(12);
 public void Thema13() => ThemaButtonClicked(13);
 public void Thema14() => ThemaButtonClicked(14);
 public void Thema15() => ThemaButtonClicked(15);
 public void Thema16() => ThemaButtonClicked(16);
 public void Thema17() => ThemaButtonClicked(17);
 public void Thema18() => ThemaButtonClicked(18);
 public void Thema19() => ThemaButtonClicked(19);
 public void Press0() => Press(0);
 public void Press1() => Press(1);
 public void Press2() => Press(2);
 public void Press3() => Press(3);
 public void Press4() => Press(4);
 public void Press5() => Press(5);
 public void Press6() => Press(6);
 public void Press7() => Press(7);
 public void Press8() => Press(8);
 public void Press9() => Press(9);
 public void Press10() => Press(10);
 public void Press11() => Press(11);
 public void Press12() => Press(12);
 public void Press13() => Press(13);
 public void Press14() => Press(14);
 public void Press15() => Press(15);
 public void Press16() => Press(16);
 public void Press17() => Press(17);
 public void Press18() => Press(18);

 public void Press19()
 {
 Press(19);
 }
}
```





 



아래는 메인인 KoreaNews코드이다.

​

우선 Start에서 언론사 수만큼 버튼을 켠다.

​

언론사 버튼이 눌려지면 맨 아래 public void Press(int pressIndex)에서 언론사의 HTML을 가져온다.

​

가져온 HTML은 OnStringLoadSuccess되어 Html태그를 제거하고 테마를 구분해 테마의 수와 종류를 버튼에 띄운다.

​

​

테마 버튼을 선택하면 ThemaButtonClicked로 가서 SetPageIndexes를 돌리고 ShowPage한다.

PageIndexes는 한 테마에서 각 페이지마다 보여줄 범위를 가진다.

​

SetPageIndexes에서는 \_(언더바)마다 나눠진 기사를 pagesize만큼 나눈 후, 각 페이지에서 어디까지 표시할지 인덱스를 저장한다.

​

사실 코드만 길 뿐이지 들어가는 로직은 없다.

생각치도 못한 숫자세기 문제와(마지막 인덱스가 넘치는 경우) 앞으로 멀티 플레이어를 위한 싱크를 제외하고는 코드만 길 뿐이다.

​

​

맨 아래의 Thema(), Press()는 테마, 언론사의 버튼이다.

버튼은 유동적으로 수가 바뀌므로 일단 최대값 20으로 맞춰놓았다.

​

아래는 버튼의 코드이다.





 




```
public void ButtonClicked()
 {
 transform.parent.parent.parent.parent.GetComponent()
 .SendCustomEvent(name.Substring(0,5)+transform.GetSiblingIndex());
 
 }
```





 



버튼의 상위 UdonBehavior를 찾은 뒤 자신의 이름 앞 5글자와 본인의 하이라키 순서를 이벤트 이름으로 보낸다.

transfor[m.parent.parent.parent.parent](http://m.parent.parent.parent.parent) 는 추하긴 하지만... GetComponentInParent보다는 낫지 않을까? 싶다.

​

아. 몰랐었는데 GetComponentInParent는 본인부터 찾기 때문에 transform.parent를 하고 GetComponentInParent을 사용해야 한다.

​

나중에 작동이 안된다면 필시 여기 부분 일 것이다.

​

​

​





 



> 
> 시연&마무리하며
> 
> 
> 잘 된다. 야호
> 
> 
> 









[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (Unity + 최적화)/3.png)](#)








아래는 간단한 시연

<https://youtu.be/Ku52Hjhq1mA>





 











글자의 크기가 가독성이 떨어지긴 하지만... 그건 이 뉴스 패널을 사용할 사람의 몫 아닐...까? ㅋㅋ

​

​

​

앞으로 시간이 난다면 해야 할 일은

​

​

SubString(최적화): SubString은 가비지를 생성하므로 StringBuilder를 사용해야 한다. 그러나 VRChat에서는 StringBuilder가 사용불가능하다. 이를 해결하기 위해서는 Remove를 사용하거나 인덱스를 이용해 각 기사에 접근하는 방법을 이용해야 한다.

​

Sync: 다른 플레이어와의 Sync를 위해서는 현재 플레이어가 보고 있는 언론사,테마,페이지를 가져와야 한다.

HTML을 가져온 후 5초간 로드가 불가능하므로, 만약 다른 플레이어가 로드를 마친 후 페이지조작을 하면 String에서 오류가 날 수 있다.

이를 위한 예외처리를 해야 한다. VRChat에서 try catch가 불가능한것은 덤...

​

​

가볍게 시작한 일인데 하루가 후딱 지나가버렸다.

​

최근 졸업작품만 하다가 내가 하고싶은 것을 하니 조금 더 편안하긴 하다.

​

​

다음에 시간만 허락한다면 실시간 증권, 날씨, 블로그도 갱신하는 걸 만들고 싶다.





 

