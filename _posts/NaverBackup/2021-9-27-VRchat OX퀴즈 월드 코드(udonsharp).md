---
title: "VRchat OX퀴즈 월드 코드(udonsharp)"
categories:
 - UDONSHARPexample
---
#VRchat OX퀴즈 월드 코드(udonsharp) : 네이버 블로그








필자는 VRchat의 OX퀴즈 월드를 만들었습니다.

혹시나 누군가에게 도움이 될까 싶어 글을 써봅니다

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/0.png)](#)








[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/1.png)](#)








일단 월드 구성은 간단합니다. 처음 로비에서 시작하여 시작 버튼을 누르면 뒤에 있는 OX 퀴즈장으로 이동하고 문제를 틀리게 되면 로비로 이동되는 구조입니다.

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/2.png)](#)








월드의 메인은 다음 문제를 작동시키는 큐브에 있습니다

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/3.png)](#)








비주얼 스튜디오로 열었을 때 나오는 변수들입니다.

​

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/4.png)](#)








public Text ReviveCount;

부활까지 남은 라운드수를 텍스트로 가지는 텍스트 변수입니다.

외부 UI 부활카운트 (Text)와 연결되어 있습니다

​

​

public AudioSource Effect;

문제 맞추는 시간 카운트 5 4 3 2 1 할때마다 나는 효과음입니다.

소리 파일을 직접 가져옵니다

​

​

bool[] timecheck = new bool[5];

1,2,3,4,5초마다 시간이 지났는지 체크합니다

​

​

public Text Kind;

분야를 저장하는 텍스트 변수입니다

외부 UI 분야(Text) 와 연결되어 있습니다

​

​

public Text Answer;

답이 O인지 X인지 저장하는 텍스트 파일입니다

외부 UI answer(Text) 와 연결되어 있브니다

​

​

public TextAsset TxtFile\_Quiz\_Utf8;

TextAsset입니다.

퀴즈 파일을 불러오는데, 퀴즈 파일은 엑셀에 저장되어 있습니다.





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/5.png)](#)








엑셀에 저장되어있는 것은 분야, 기출문제, 답, 기출해설 4가지가 있습니다

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/6.png)](#)








이를 유니코드 텍스트로 저장 하면

​

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/7.png)](#)








텍스트 파일이 만들어지는데 4개의 분류를 탭으로 구별합니다.

빨간색으로 그린 부분이 구별하는 부분입니다.

​

​

​

​

​

​

public Text MainText;

메인 텍스트는 문제가 저장되는 부분입니다.

외부 UI 문제(Text)와 연동되어 있습니다

​

​

​

​

public Text TimeText;

타임 텍스트는 시간을 텍스트로 저장합니다

타이머(Text)와 연결되어 있습니다

​

​

public Text LevelText;

레벨 텍스트는 몇 라운드가 진행되었는지를 저장합니다

level(Text)와 연결되어 있습니다 

​

public Text peopleCountText;

피플카운트텍스트는 OX퀴즈장 내에 얼마나 많은 사람들이 있는지를 저장합니다

​

​

[UdonSynced] int temp;

temp는 랜덤으로 한 숫자를 골라 저장하는 변수입니다

싱크가 되어 있습니다

​

​

[UdonSynced] int Level = 0;

현재까지 진행된 라운드 수를 저장합니다.

싱크가 되어 있습니다

​

​

[UdonSynced] int peopleCount;

OX퀴즈장 내의 플레이어 수를 저장합니다.

싱크가 되어 있습니다

​

[UdonSynced] int time\_temp = 0;

문제 결과가 나올 때 까지의 타이머입니다.

싱크되어 있습니다

​

bool ready;

다음 문제를 낼 준비가 되었는지를 저장하는 bool형 변수입니다

​

bool ready\_onec;

문제 출제 중 한번만 해야 하는 과정을 했는지를 저장하는 bool형 변수입니다

​

int time\_temp\_start = 0;

시간을 잴 때 기준이 되는 변수입니다

​

string String\_Quiz;

퀴즈 전체를 불러옵니다

​

string[] Array\_Quiz;

퀴즈 파일 중 엔터로 분류하여 저장합니다

이 문자열에는 분야 문제 답 해설 이 저장됩니다

그리고 배열로 선언되었는데 

Array\_Quiz[] []내에는 문제 번호가 들어갑니다

​

string[] Array\_Quiz\_detail;

위의 Array\_Quiz를 탭으로 분류합니다

 Array\_Quiz\_detail[0]: 분야

 Array\_Quiz\_detail[1]: 문제

 Array\_Quiz\_detail[2]: 답

 Array\_Quiz\_detail[3]: 문제 해설

을 저장합니다

​

public Vector3 location\_die;

플레이어가 죽은 후 돌아가는 위치를 가집니다

​

​

Vector3 o\_position;

큐브가 원래 있던 위치를 가집니다

​

​

public Quaternion Quater;

이동할 때 방향과 회전각을 가집니다

​

public UdonBehaviour Teleport;

텔레포트 버튼을 작동하는 우동 파일입니다

플레이어가 부활 할 때 Start버튼을 재생성 할 때 필요합니다

​

​

public Vector3 locationCenter;

위 이미지에는 있지만 쓰지 않는 변수입니다. 블로그 쓰면서 삭제했습니다.

​

​

​

​

​

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/8.png)](#)








월드에 들어 온 후 처음으로 코드가 실행되는 void Start() 입니다

​

​

​

String\_Quiz = TxtFile\_Quiz\_Utf8.ToString();

문제 파일인 TxtFile\_Quiz\_Utf8을 String으로 변환 한 후 String\_Quiz에 저장합니다

​

​

​

​

Array\_Quiz = String\_Quiz.Split('\n');

위 코드에서 저장한 String\_Quiz을 \n으로 나눈 후 Array\_Quiz에 저장합니다

split은 특정 문자를 기준으로 나누는 기능이 있습니다

​

Array\_Quiz는 크기가 없이 선언된 배열이므로 문제 수와 상관 없이 Array\_Quiz에 담깁니다.

예시로 Array\_Quiz[1]에는 

상식 미국의 수도는 뉴욕이다 X 미국의 수도는 워싱턴DC이다\

​

와 같이 한 문제가 담겨 있습니다.

​

​

​

​

​

​

​

​

o\_position = this.transfor[m.position;](http://m.position;)

현재 지금 오브젝트 위치인 this.transfor[m.position](http://m.position;)을 o\_position에 저장합니다

this는 스스로의 객체를 의미합니다.

​

​

SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "PlayerIsJoin");

Start는 플레이어가 처음 들어왔음을 의미하므로 PlayerIsJoin을 커스텀 네트워크 이벤트로 실행합니다

​

커스텀 네트워크 이벤트는 기본 이벤트( start, update)외에 새로운 이벤트를 실행 할 수 있습니다

SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEvent**Target.All**, "PlayerIsJoin");은 모든 Target, 즉 모든 플레이어에게 PlayerIsJoin이라는 이름을 가진 이벤트를 실행하게 합니다

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/9.png)](#)








이건 코드 아래에 있는 PlayerIsJoin 함수입니다.





 




```
public void PlayerIsJoin()
 {
 if(Networking.IsOwner(this.gameObject)) //플레이어가 이 게임 오브젝트의 오너라면
 RequestSerialization(); //변수 동기화를 요청합니다
 }
```





 



Networking.IsOwner(this.gameObject)는 this.gameObject가 자신의 소유인지 확인합니다.

자신의 소유인지 확인 하는 이유는

동기화 된 변수의 기준은 소유자가 하는 것이 오류가 적기 때문입니다.

소유자가 아닌 다른 플레이어가 동기를 하게 되면 잘못된 값으로 동기가 될 수 있습니다.

​

RequestSerialization()는 vrchat내의 변수를 동기화하는 기능을 가집니다.

소유자임을 확인 한 후 동기를 시킵니다.

그럼 새로운 플레이어가 왔을 때도 변수를 동기 시킬 수 있습니다,

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/8.png)](#)








다시 Start로 돌아와서

​

if (Networking.IsOwner(this.gameObject)) //이 오브젝트의 소유자라면

{

Level = 0; 레벨(라운드)을 0으로 초기화

peopleCount = 0; 사람 수를 0으로 초기화

RequestSerialization(); 직력화를 한번 수행합니다.

}

​

​

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/11.png)](#)








다음은 Interact(작동)입니다.

Interact는 override를 해주셔야 합니다

​





 




```
if (!Networking.IsOwner(this.gameObject)) //이 오브젝트의 소유자가 아니면
 {
 Networking.SetOwner(Networking.LocalPlayer, this.gameObject);
 //작동한 플레이어를 이 게임오브젝트의 소유자로 설정합니다
 }
 timecheck[0] = false;
 timecheck[1] = false;
 timecheck[2] = false;
 timecheck[3] = false;
 timecheck[4] = false;
 //1초에서 5초가 지났는지 확인하는 배열 timecheck를 false로 초기화힙니다
 //다른 방법이 있긴 할텐데 그냥 5번 쳤습니다.

 ready = true;
 ready\_onec = true;
 //ready는 다음 문제를 낼 준비
 //ready\_onec는 다음 문제를 낼 때 한번만 해야 하는 과정이 필요한지를 체크합니다
 

 temp = UnityEngine.Random.Range(1, Array\_Quiz.Length);
 //void start에서 "\n"(엔터키)로 분류된 배열 Array\_Quiz를
 //1에서 배열의 길이 중 랜덤 숫자 하나를 temp에 저장합니다
 
 Level++;//한번 작동함은 다음 문제를 내는 것을 의미합니다. 레벨(라운드)수를 올려줍니다
 RequestSerialization(); //변수들을 모두 초기화, 저장 했으면 동기화를 한번 해줍니다
 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "PeopleCountSet");
 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "HideCube");
 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "AnswerSetZero");
 //위 세개의 이벤트는 아래에서 설명하겠습니다
```





 



PeopleCountSet은 몇명이 생존했는지 텍스트를 설정하는 이벤트입니다.

peopleCountText.text = peopleCount.ToString() + "명 생존";

peopleCount는 OX장에 플레이어가 몇명이 있는지를 저장합니다

​

HideCube는 큐브를 숨기기 위해 위치를 옮깁니다

this.transfor[m.position](http://m.position) = new Vector3(0, -10, 0);

문제를 내는 도중 문제를 내는 큐브를 숨기기 위해 큐브의 위치를 옮깁니다

위치를 0,-10,0으로 옮깁니다

​

​

AnswerSetZero는 답의 부분을 공백으로 바꾸는 이벤트입니다

Answer.text = "";

답이 저장되는 Answser.text를 공백으로 채웁니다

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/12.png)](#)








이제 Update부분입니다.

Update는 프레임마다 호출되는 함수입니다. 

이 코드에서는 문제가 제출되고 문제를 푸는 시간과 문제의 결과(틀리면 아웃)을 결정합니다

if(ready)로 문제가 풀 ready가 되었는지 체크합니다

ready 는 전에 Interact에서 true로 변경해 두었습니다.

​

위 코드는 if로 코드들을 다 접어둔 것입니다.

간단하 if별로 보면

​

if(ready\_once)

if(time\_temp<5)

if(time\_temp<-1)

if(time\_temp<0)

​

네가지가 있습니다

if(ready\_once) 는 update를 할 때 한번 수행되어야 할 작업을 실행합니다

if(time\_temp<5) time\_temp는 문제 해결까지 남은 시간입니다 

각각 5,-1,0은 답 확인 5초전, -1초전, 0초를 의미합니다. -1초전은 문제 확인 후 1초후를 의미합니다

if(time\_temp<-1)

if(time\_temp<0)

​

​

if(ready\_once) 부터 보겠습니다.





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/13.png)](#)








​

if (ready\_onec)

{

time\_temp\_start = ((int)Time.time);

ready\_onec = false;

SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "ArrayDetail");

SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "QuizSet");

SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "LevelSet");

SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "SetKind");

SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "SetReviveCount");

}

time\_temp = 15 - (((int)Time.time) - time\_temp\_start); //시간제한 숫자

​

​

한 줄 씩 보겠습니다

if (ready\_onec)

{

time\_temp\_start = ((int)Time.time); //time\_temp\_start에 현재 시간인 Time.time의 정수형을 저장합니다.

ready\_onec = false; ready\_onec는 한번만 작동하면 돼니깐 false로 둡니다

SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "ArrayDetail");

//ArrayDetail 이벤트를 실행합니다

ArrayDetail 이벤트는

public void ArrayDetail()

{

 Array\_Quiz\_detail = Array\_Quiz[temp].Split('\t');

}

입니다.

즉 전 과정 Interact에서 temp에 출제할 문제 랜덤 숫자를 넣었습니다.

Array\_Quiz[temp]에는 랜덤 문제가 담겨있겠지요.

이 문자열에는 분류 문제 답 해설 이 4가지가 탭으로 분류 되었습니다

탭으로 분류 됀 것을 나누기 위해 Array\_Quiz를 \t 로 나눕니다. \t는 아스키 코드로 탭입니다

나누는 기능은 Split 이 합니다.

나눠진 문자열 배열은 Array\_Quiz\_detail에 저장됩니다.

​

예시로 Array\_Quiz[temp]에는 본문의 temp번째 문장은

상식 우리나라에서 해는 동쪽에서 뜬다 O 해설:우리나라에서 해는 동쪽에서 뜬다

라고 저장되어 있다고 한다면

나누어진 Array\_Quiz\_detail은

Array\_Quiz\_detail[0]은 상식

Array\_Quiz\_detail[1]은 우리나라에서 해는 동쪽에서 뜬다

Array\_Quiz\_detail[2]는 O

Array\_Quiz\_detail[3]은 해설:우리나라에서 해는 동쪽에서 뜬다

가 된다.

​

나눠진 것은 분야,문제,답,해설입니다.

문제를 제출하면서 필요한 부분은 분야와 문제입니다.

따라서 문제와 분야를 텍스트로 띄어야 합니다

​

SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "QuizSet");

//퀴즈를 텍스트로 띄우는 이벤트 QuizSet을 실행합니다

​

void QuizSet()

{

 MainText.text = Array\_Quiz\_detail[1];

}

퀴즈셋입니다

MainText.text에 Array\_Quiz\_detail[1]을 넣습니다. Array\_Quiz\_detail[1]은 문제가 들어있는 문자열입니다

​

​

​

​

SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "LevelSet");

//레벨(라운드)를 텍스트로 띄우는 이벤트 LevelSet을 실행합니다

public void LevelSet()

{

LevelText.text = Level.ToString() + "번문제";

}

LevelText.text에 Level의 문자열형을 넣습니다. 

​

​

SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "SetKind");

SetKind는 분류를 텍스트로 띄웁니다

위 2개와 비슷하므로 설명은 건너뛰겠습니다

​

​

SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "SetReviveCount");

부활까진 남은 라운드 수를 텍스트로 띄웁니다. 위와 같으므로 건너뛰겠습니다.

}

​

여기까지가 다음 문제 버튼이 작동됬을때 한번 실행해야하는 코드입니다.

​

나머지는 update에서 프레임마다 반복되는 과정입니다

time\_temp = 15 - (((int)Time.time) - time\_temp\_start); //시간제한 숫자(15-현재시간+시작시간)

15초에서 지나간 시작을 뺍니다. 즉 문제 종료까지 남은 시간이 time\_temp에 저장됩니다

답 공개까지 1초가 남을 땐 time\_temp에 1이 들어가 있습니다.

​

나머지 if문은 time\_temp(남은시간)을 비교합니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/14.png)](#)








​





 




```
if (time\_temp < 5)//4초 이내
 if (time\_temp > -1)//문제 종료후 1초 이후까지
 {
 if (timecheck[time\_temp] == false)
 //time\_temp는 4, 3, 2, 1, 0 순으로 줄어듭니다
 //처음 time\_temp에는 모두 false 값이 들어 있습니다. 즉 1초마다 아래 코드가 실행됩니다
 {
 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "EffectOn");
 //이펙트 온 이벤트는 소리가 나는 이벤트입니다
 //Effect.Play();를 하면 Effect라는 소리 소스의 파일을 재생 할 수 있습니다
 timecheck[time\_temp] = true;
 //1초가 지나갔음이 확인 되면 true로 변경해 1초마다 실행되게 합니다.
 }


 RequestSerialization();
 //변수들을 동기를 한번 시킵니다.
 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "TimeSet");
 //타이머를 텍스트로 표시합니다
 }


 if (time\_temp < -1) //남은 시간이-1보다 작은 상태. 즉 게임이 끝난 후를 의미합니다
 {
 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "TimeSetZero");
 //남은 시간 타이머를 빈칸으로 설정합니다
 if (Level % 10 == 0)//레벨(라운드)가 10배수라면 부활시킵니다
 {

 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "Revive");
 //리바이브라는 부활시키는 이벤트를 실행시킵니다.

 }

 }
```





 




```
if (time\_temp < 0)//남은 시간 0초 아래, 즉 게임이 끝난 후를 의미한다.
 {
 if (Array\_Quiz\_detail[2] == "O")
 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "LeftTeleport");
 if (Array\_Quiz\_detail[2] == "X")
 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "RightTeleport");
 //답이 O인지 X에 따라 왼쪽 또는 오른쪽에 있는 플레이어를 모두 이동시킨다(탈락)
 //답은 Array\_Quiz\_detail[2]에 O 또는 X로 저장되어 있다.

 if (time\_temp < -1)
 {
 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "ResetCube");
 //인터랙트를 했을 때 큐브를 한번 더 클릭하지 못하도록 큐브를 숨겨 두었다. 게임이 끝났으니 다시 원위치

 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "AnswerWhySet");
 //해설을 텍스트로 띄운다.

 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "AnswerSet");
 //답을 텍스트로 띄운다.

 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "PeopleCountSet");
 //틀린 답의 플레이어는 탈락한 후 플레이어 수를 업데이트한다.

 ready = false;
 //update를 끝내기 위해 ready를 false로 둔다.

 if (peopleCount <= 0)//people카운트가 0이하이면, 즉 게임 오버를 의미한다.
 {
 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, " MainTextPlusGameOver");
 //게임 오버 이벤트를 실행한다.
 }

 }


 }
```





 



이로써 OX퀴즈 월드의 중심 코드를 소개했습니다

​

​

​

나머지 코드는 게임 입장 버튼이 있습니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/15.png)](#)









```
public Vector3 location\_quiz; //퀴즈장의 벡터3위치입니다
 public Quaternion Quater; //회전을 의미합니다.
 void Start()
 {
 
 }

 public override void Interact() //작동하면
 {
 Networking.LocalPlayer.TeleportTo(location\_quiz, Quater);//작동한 로컬 플레이어를 텔레포트 시킵니다
 this.gameObject.SetActive(false); //시작 큐브를 비활성화 시킵니다.

 }
 public void TurnOnTeleportButton()
 {
 this.gameObject.SetActive(true); //메인의 코드에서 부활 이벤트가 실행되거나 리셋이 되었을 때 버튼을 활성화합니다
 }
```





 



​

​

​

​

​

다음은 OX퀴즈장 내 플레이어 수를 체크하는 checkpeople 코드입니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-27-VRchat OX퀴즈 월드 코드(udonsharp)/16.png)](#)









```
public UdonBehaviour Main; //메인 프로그램을 가져옵니다.
 void Start()
 {



 }
 public override void OnPlayerTriggerEnter(VRCPlayerApi player)//트리거인 콜라이더 내에 플레이어가 들어오면
 {
 Main.SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "Main\_PlayerAdd");
 //메인에 있는 이벤트인 Main\_PlayerAdd를 실행시킵니다. Main\_PlayerAdd은 플레이어 수를 1증가시키는 이벤트입니다.
 }
 public override void OnPlayerTriggerExit(VRCPlayerApi player)//트리거인 콜라이더에서 플레이어가 나가면
 {
 Main.SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All,"Main\_PlayerSub");
 메인에 있는 Main\_PlayerSub를 실행시킵니다. 이는 플레이어 변수에서 1을 빼는 코드입니다.
 }
```





 



위 코드처럼 외부에 있는 코드를 불러와 실행 할 수도 있습니다.

​

​

​

​

이로써 VRchat OX퀴즈 Udon 코드 설명을 마치겠습니다

궁금한 점은 디스코드 rage147#2898로 물어봐주세요!

​

​

첨부파일에 소스 코드 올려두겠습니다!





 



**첨부파일**

udonsharp.cs

[파일 다운로드](https://blogattach.naver.net/74e168dbc095904c608ee6d3ea0e760cacfe0be887/20210927_271_blogfile/dls32208_1632728010030_xVfK1M_cs/udonsharp.cs)




 



메인입니다!

​





 



**첨부파일**

teleport.cs

[파일 다운로드](https://blogattach.naver.net/74e168dbc095904c608ee6d3ea0e760cacfe0be887/20210927_189_blogfile/dls32208_1632728029911_80lHYv_cs/teleport.cs)




 



텔레포트입니다!

​

​





 



**첨부파일**

reset.cs

[파일 다운로드](https://blogattach.naver.net/79ec65d5c49b9d416d83ebdee7037b01a1f306e57a/20210927_31_blogfile/dls32208_1632728041594_6e3jGv_cs/reset.cs)




 



리셋 큐브입니다!

​

​





 



**첨부파일**

checkpeople.cs

[파일 다운로드](https://blogattach.naver.net/28bd348790c5cc103cd2ba8fb6522a50f0a257b447/20210927_244_blogfile/dls32208_1632728056331_W5PG9o_cs/checkpeople.cs)




 



플레이어 수를 세는 코드입니다!(콜라이더)

​

​

​

​

​

아래는 단순히 오브젝트를 활성화/비활성화 하거나 음악을 키거나 끄는 기능뿐입니다

​





 



**첨부파일**

music.cs

[파일 다운로드](https://blogattach.naver.net/0e9b12a1bbefea361af49ca990740c76d68471925c/20210927_221_blogfile/dls32208_1632728173910_Hs2v4K_cs/music.cs)




 



음악을 키고 끄는 기능입니다

​

​





 



**첨부파일**

soundeffect.cs

[파일 다운로드](https://blogattach.naver.net/6ffa73c3d38d8b577b95fdc8f1156d17b7e510f3df/20210927_262_blogfile/dls32208_1632728088334_OCjJFp_cs/soundeffect.cs)




 



배경 음악입니다

​

​





 



**첨부파일**

mirror.cs

[파일 다운로드](https://blogattach.naver.net/26b33a899fc7c21e32dcb481b85c245efeac59ba78/20210927_25_blogfile/dls32208_1632728072644_0aOIW8_cs/mirror.cs)




 



거울입니다





 

