---
title: "Udon Network에 관해서"
categories:
 - UDONrelatedarticle
---
#Udon Network에 관해서 : 네이버 블로그








*본 글은 VRChat 2023캘린더의 1월 17일 글입니다*

<https://rage147-owo.github.io/2023HappyNewYearCalendar/>





 



[![](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fraw.githubusercontent.com%2Frage147-OwO%2F2023HappyNewYearCalendar%2Fmain%2F%25EA%25B8%2580%25EC%259D%2584%25EA%25B8%25B0%25EB%258B%25A4%25EB%25A6%25AC%25EA%25B3%25A0%25EC%259E%2588%25EC%2596%25B4.png%22&type=ff500_300)](https://rage147-owo.github.io/2023HappyNewYearCalendar/)
[2023 신년맞이 VRChat 캘린더 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 1월 1일 steen VRChat 월드 최적화 기법 1월 2일 R3C0D3r 오클루젼 컬링에 대하여 1월 3일 GomRang熊娘 한국어학습박물관 월드 제작 기법 "프로젝터" 소개 1월 4일 > 1월 5일 R3C0D3r VRChat 한국어 튜토리얼 포스터 게시판의 작동 원리 1월 6일 > 1월 7일 1월 8일 > 1월 9일 1월 10일 HYPHERL...


rage147-owo.github.io](https://rage147-owo.github.io/2023HappyNewYearCalendar/)




 



**​**

**​**





 





---





 



**0. 시작하며**

안녕하세요! 2023년이 밝았습니다!

오늘의 주제로는 Udon 네트워크를 다뤄 볼까 합니다!

​

여러분은 월드제작을 하면서 네트워킹에서 어려움을 겪었었나요?

저는 VRChat게임 월드를 만들면서 고생을 많이 했었는데, 가장 큰 어려움으로는 

**검색해도 나오는 정보가 적다**였습니다

​

VRChat Udon은 넓은 게임들 중 마이너한 장르이고, 

아바타가 아닌 월드는 더 마이너하며

그 중에서도 Udon의 네트워크는

검색해서 배우는 시간보다 혼자 실험하는 시간이 더 많았습니다

​

그렇기에 오늘 글을 기회 삼아 누군가에게는 소중한 지식의 양분이, 누군가에게는 놓쳤던 팁을 알게 되는 글이 되었으면 좋겠습니다.

​

​

* p.s 글 중에 잘못된 내용이 있을 경우 Discord: rage147#2898 로 DM주세요!
* p.p.s 문서를 참고하면 좋습니다! <https://docs.vrchat.com/docs/udon-networking>

​

​

​

**1. Udon네트워크의 다양한 개념**

​

**싱크(Sync)**란 오브젝트의 정보를 다른 플레이어도 같게끔 동기하는 것입니다.

​

**로컬**은 자기에게만 실행되는 오브젝트을 말하고

**글로벌**은 모든 플레이어에게 실행되는 **싱크된 오브젝트**입니다

​

**오너쉽(Ownership)**이란 싱크의 기준이 될 수 있는 권리입니다.

**오너(Owner)**란 싱크의 기준이 되는 플레이어입니다. 

모든 싱크된 오브젝트는 오너를 가지고 있습니다.

**마스터(Master)**란 월드 인스턴스의 기준이 되는 플레이어입니다. 한 플레이어가 오너쉽이 많은 경우, 마스터가 그 플레이어에게로 넘어가기도 합니다.

​

​

예시로, 픽업 물체가 하나 있다고 할 때,

로컬은 자신에게만 보이는 물체입니다.

글로벌(싱크된 오브젝트)는 모두에게 보이는 물체입니다.

​

픽업 물체는 물체를 들고 있는 사람이 오너가 되고, 다른 사람이 집으면 오너가 바뀝니다.

즉 오브젝트의 위치가 들고 있는 사람을 기준으로 싱크됩니다.

만약 싱크드된 오브젝트의 오너가 월드를 나간다면, 오브젝트의 오너쉽은 마스터가 가지게 됩니다.

​

**싱크모드(SyncMode)**란 Udon Behaviour에서 싱크를 하는 방식입니다

None은 오너가 정해지지 않고 SendNetworkingEvent가 불가능합니다

Continuous는 싱크 변수를 항상 동기시킵니다

Manual은 싱크 변수를 수동으로 동시시켜줘야 합니다

싱크 모드는 아래 싱크의 방법 중 싱크드된 변수에서 한번 더 다루겠습니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-1-21-Udon Network에 관해서/0.png)](#)








​

​

​

**2. Sync의 방법**

지루한 개념을 지나 싱크의 방법입니다.

싱크의 방법으로는 여러 가지 방법이 있습니다.

​

협정세계시(UTC)를 기준으로 싱크하는 방법.

비디오 플레이어를 통해 싱크하는 방법,

아바타를 이용해 싱크하는 방법 등등 다양합니다.

​

하지만 오늘 글에서는 딱 3가지 싱크만 다뤄 보도록 하겠습니다

- VRCObjectSync

- 샌드커스텀네트워크를 이용한 싱크

- 싱크 변수

​

**- VRC Object Sync**

문서: <https://docs.vrchat.com/docs/vrc_objectsync>

문서: <https://docs.vrchat.com/docs/network-components#vrc-object-sync>

VRC Object Sync 컴포넌트는 오브젝트의 

**VRC Object Sync**는 오브젝트 활성화 비활성화, Transform과 Rigidbody를 동기시킵니다

오직 오브젝트의 오너만 값을 변경 할 수 있습니다

싱크모드를 Continuous로 해야지 작동합니다

보통 픽업 물체에 ObjectSync 를 넣어 글로벌 오브젝트를 만듭니다

Allow Collision Ownership Transfer를 체크하면 다른 사람의 오브젝트와 충돌 시, 소유권을 가져옵니다

쓸데 없는 버그를 피하기 위해 체크를 해제하는 편입니다.





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-1-21-Udon Network에 관해서/1.png)](#)








장점: 픽업 오브젝트, 활성화/비활성화, Transform, Rigidbody 동기가 필요한 경우 간편하게 적용 할 수 있음

단점: 

싱크모드가 Continuous로 고정됨으로 해당 오브젝트의 우동 코드에 많은 싱크변수를 넣을 수 없습니다

픽업 오브젝트인 경우 픽업 할 때마다 오너가 바뀌므로 오브젝트를 활성화/비활성화 할 때 주의가 필요합니다

싱크 속도가 느린 편입니다. 특히 충돌을 감지 할 때 오너가 아닌 경우에는 감지가 정확하지 않을 수 있습니다

**​**

**​**

**- 샌드커스텀네트워크를 이용한 싱크**

문서: <https://docs.vrchat.com/docs/udon-networking#using-custom-events>

샌드 커스텀 네트워크는 Udon에서 이벤트를 네트워크로 보내주는 방법입니다

싱크모드가 None이면 작동하지 않습니다

\_(언더바)로 시작하는 이벤트 이름은 샌드커스텀네트워크이벤트를 사용 할 수 없습니다

​

특정 이벤트를 보내주기 때문에 미리 만들어놓은 이벤트만 가능합니다

Open과 Close같이 정해진 이벤트를 실행하는데 적합합니다

타겟은 All은 모두에게 Owner는 오브젝트의 오너에게만 이벤트를 실행합니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-1-21-Udon Network에 관해서/2.png)](#)








샌드커스텀네트워크이벤트가 실행되면 현재 있는 플레이어들에게만 이벤트가 일어나기 때문에

늦게 들어온 플레이어인 경우에는 따로 싱크를 해 주어야 합니다

예를 들어 문을 여는 버튼이 있고, 샌드커스텀네트워크이벤트로 문을 열었을 때,

늦게 들어온 플레이어는 이벤트를 받지 못했으니 문이 닫혀 있는 상태입니다.

그렇기에 오브젝트의 오너가 문이 열려있나 닫혀있나 판별 한 후 한번 더 샌드커스텀네트워크 이벤트를 해주어야 합니다.

​

예제입니다. 문이 열려있나 아닌지 Bool IsOpened로 판별합니다

플레이어가 조인하면, 오너가 문이 열려있는경우 샌드커스텀네트워크 이벤트를 해줍니다

기존 문이 열여있는 플레이어가 문이 두번 열리는 것을 방지하기 위해 IsOpened가 False(기본값)일때만 실행되게 합니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-1-21-Udon Network에 관해서/3.png)](#)









```
application/vnd.unity.graphview.elements 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
```





 



팁으로 이벤트의 이름에 인자를 넣는 식으로 사용 할 수 있습니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-1-21-Udon Network에 관해서/4.png)](#)








그래프에서는 사용하기 어렵지만 U#에서는 편리합니다

​

아래와 같은 방식으로 사용 할 수 있습니다.

커스텀이벤트는 public void ()의 형식입니다





 




```
private int Number = 0;
 public override void Interact()
 {
 SendCustomNetworkEvent(NetworkEventTarget.All,"Event"+Number);
 }

 private void Event(int value)
 {
 Debug.Log(value);
 }
 public void Event0()
 {
 Event(0);
 }
 public void Event1()
 {
 Event(1);
 }
}
```





 



이벤트를 여러 개 만드는 것은 유저가 만들어 놓은 도구가 있습니다

​

글: <https://ask.vrchat.com/t/how-to-send-variables-over-network-udonsharp/2282>

도구: <https://github.com/Reimajo/HorribleUdonNetworkingCodeGenerator>

​

아래와 같이 사용 할 수 있습니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-1-21-Udon Network에 관해서/5.png)](#)








샌드커스텀네트워크이벤트의 장점으로는

네트워크 트래픽을 적게 먹는다

싱크가 늦더라도 안전하게 작동된다

적은 양이지만 인수를 보낼 수 있다

​

단점으로는

싱크 속도가 느린 편이다

나중에 들어오는 플레이어의 싱크를 생각하기 귀찮다

그래프에서는 이벤트를 여러개를 만들기 어렵다

​

추후에 글을 쓸 예정이지만 싱크변수의 양이 많고, 변수를 동기하거나 오너가 바뀌는 경우 네트워크 트래픽을 순간적으로 많이 잡아먹습니다. 

 게임 월드이고 한 오브젝트에 변수가 많이 들어 있는 경우에는 트래픽에 의한 렉이 많이 걸립니다.

그렇기에 샌드커스텀네트워크이벤트를 적재적소에 사용하면 유한한 네트워크 트래픽을 쪼개 사용 할 수 있습니다

​

p.s 샌드커스텀네트워크이벤트를 오너로 해서 특정 버튼을 누르면 오너가 판단해서 실행하게끔 코드를 짤 수 있습니다

​

**- 싱크변수**

문서: <https://docs.vrchat.com/docs/udon-networking#variables>

싱크변수는 우동비헤이버의 변수를 싱크하는 방식입니다

bool, char, byte, sbyte, short, ushort, int, uint, long, ulong, float, double, Vector2, Vector3, Vector4, Quaternion, string, VRCUrl, Color and Color32를 싱크 할 수 있습니다

변수의 크기는 Photon과 동일합니다(<https://doc.photonengine.com/en-us/realtime/current/reference/serialization-in-photon>)

싱크 변수는 늦게 들어온 플레이어도 같은 값을 가집니다

**오너만 값을 바꿀 수 있습니다**

**​**

싱크변수는 말 그대로 변수를 싱크 할 때 사용합니다

슬라이더 값(float)을 싱크하거나

월드 내에 점수판(string)을 싱크할 수 있습니다

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-1-21-Udon Network에 관해서/6.png)](#)








그래프에서는 변수 탭에서 synced를 체크하면 됩니다

smooth는 전의 값과 싱크된 값의 보간입니다

아래 문서에 자세히 나와 있습니다

문서: <https://hatuxes.hatenablog.jp/entry/2020/04/05/013323>

​

아래는 U#에서의 싱크 변수 선언입니다

팁으로 애트리뷰트 [UdonBehaviourSyncMode(BehaviourSyncMode.Manual)]을 사용하면 코드에서 싱크모드를 고정 할 수 있습니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-1-21-Udon Network에 관해서/7.png)](#)








​

​

​

​

​

싱크모드가 continuous인 경우 우동비헤이버에서 계속 변수를 싱크합니다

싱크모드가 manual인 경우 수동으로 requestserialization을 해줘야 합니다

오너만 requestserialization이 가능하고 requestserialization시 값이 동기됩니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-1-21-Udon Network에 관해서/8.png)](#)








​

싱크모드가 메뉴얼인 경우 싱크 속도가 매우 빠릅니다

싱크모드에 따른 최대 전송량의 제한이 있습니다. 

하지만 전송량 제한에 못미쳐도 싱크량이 많으면 싱크 시 렉이 걸립니다

문서: <https://docs.vrchat.com/docs/network-details>

​

​

Deserialization은 requestserialization을 받는 경우 실행됩니다

오너는 실행되지 않습니다

requestserialization을 통해 싱크변수의 값이 바뀐 경우 특정 기능을 실행한다면 

OnvalueChange를 사용 할 수 있습니다

주의할 점은 플레이어가 처음 들어온 경우 requestserialization이 자동으로 실행되고 들어온 플레이어에게는 OnvalueChange가 실행됩니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-1-21-Udon Network에 관해서/9.png)](#)








​

VRChat에서 가장 빠른 싱크 방법이 bool, byte 동기이기 때문에

byte를 타이밍 감지용으로 쓸 수 있습니다

처음 플레이어가 들어올 때 OnvalueChange 가 실행되므로 처음을 무시하는 코드를 작성하면 좋은 싱크 코드가 됩니다

이에 관해서는 추후 글을 쓰겠습니다

​

​

​

싱크변수 장점:

늦은 플레이어의 동기가 편하다

manual 동기인 경우 동기가 빠르다

​

단점:

continuous 동기인 경우 계속 동기를 시도하기 때문에 트래픽을 잡아먹는다

manual 동기인 경우 동기 타이밍을 생각해줘야 한다

오너가 아닌 경우에는 동기를 할 수 없기에 누가 오너인지 생각해줘야 한다

셋오너를 하는 경우 싱크 변수가 많으면 순간 렉이 걸릴 수 있다

​

​

​

​

​

**- 디버깅 창에서 네트워크 보기**

​

VRChat에서 지원하는 디버깅 창이 있습니다

​<https://docs.vrchat.com/docs/world-debug-views>

​

오른쪽 Shift + `(~)키+6번 : 오브젝트의 이름 오너 상태 네트워크 크기 동기시간 을 볼 수 있습니다

Size,Bps, 의 값과 Happy/Suffering 으로 네트워크 상태를 볼 수 있습니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-1-21-Udon Network에 관해서/10.png)](#)








보통 네트워크에서 렉이 안걸릴 정도는 

80명 기준

In 200kb/s

Out 50kb/s

이었습니다

​

나중에 네트워크 최적화는 추후에 글을 쓸 예정입니다

​

​

**- 글을 마치며**

VRChat을 하며 유니티를 배운지 벌써 2년이 지났습니다

처음 배웠을 때의 Udon Network는 억까의 나날들이었지만, 지금은 조금 익숙 해 진 듯 합니다

두서없이 글을 생각나는대로 쓰다 보니 빠트린 부분이 많을까 걱정이 됩니다

또 누군가는 글을 읽으며 도움이 될 거라는 사실에 보람차기도 합니다

동시에 앞으로의 VRChat 월드 제작자들을 위해 많은 글을 써야 할 필요성을 느끼기도 했습니다

​

* 컴포넌트, 레이어
* 네트워크 최적화
* 플레이어를 특정하는 방법
* U# 전체적인 꿀팁

​

등등등... 2023년 신년맞이 글로 가볍게 쓰려던 글이 어느 새 무거워져만 가는 것 같습니다

​

​

슬쩍 홍보를 하자면 아래는 KoreaUdonCommunity 디스코드 서버입니다

그럼 다들 새해 복 많이 받으세요~~

<https://discord.gg/E8rF9uTggA>





 



[![](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fcdn.discordapp.com%2Fsplashes%2F745319884690554941%2F1a2864782db166ed130db201629457c7.jpg%3Fsize%3D512%22&type=ff500_300)](https://discord.gg/E8rF9uTggA)
[**Join the Korea Udon Community Discord Server!**
VRChat 월드 제작자 서버입니다. 월드 제작과 관련된 이야기를 나눠보세요! 월드 제작 뉴비분들도 환영합니다! | 377 members


discord.gg](https://discord.gg/E8rF9uTggA)




 



​





 

