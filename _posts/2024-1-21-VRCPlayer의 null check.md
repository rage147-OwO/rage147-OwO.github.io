title: "VRCPlayer의 null check"
categories:
 - UDONrelatedarticle
---
#VRCPlayer의 null check : 네이버 블로그








Udon으로 멀티 플레이어 게임을 개발할 때, 종종 마주치게 되는 문제 중 하나는 VRCPlayerAPI 변수의 Null 체크입니다. 

​

VRCPlayerAPI는 Udon에서 플레이어 정보를 다루는 클래스로, 특히 플레이어가 방을 나가거나 존재하지 않는 경우에 오류가 발생하는 경우가 많습니다. 오늘 글에서는 플레이어를 따라가는 오브젝트를 만들 때, 일어날 수 있는 Error와 null check 방식을 소개하고자 합니다

​

​

네트워킹에 대한 기본 내용은 설명하지 않으니, 네트워킹에 관한 글은 아래 글을 먼저 읽어보세요!

<https://blog.naver.com/rage147-owo/222990230516>





 



[![](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fblogthumb.pstatic.net%2FMjAyMzAxMjFfMjY3%2FMDAxNjc0MjMyNDU3MTM5.hjEW0L9aTxF5MhjKqZtT8zIgAjDZvi-rw06VVrfpXCEg.vVUJZ9yk2JN8H5C0aSoUPQXw6wLL70kYnNPaOxvGv-Ig.PNG.dls32208%2Fimage.png%3Ftype%3Dw2%22&type=ff120)](https://blog.naver.com/rage147-owo/222990230516)
[**Udon Network에 관해서**
본 글은 VRChat 2023캘린더의 1월 17일 글입니다 https://rage147-owo.github.io/2023HappyNewYearC...


blog.naver.com](https://blog.naver.com/rage147-owo/222990230516)




 



​

​

​

​

​

​





 



> 
> Case1. Update에서 GetOwner는 플레이어가 나가더라도 유효할까?
> 
> 
> 









아래와 같이 오너를 따라가는 코드를 작성 한뒤, 만약 오너가 월드를 나간다면 어떤 일이 발생할까요?





 




```
public class temp : UdonSharpBehaviour
{
 private void Update()
 {
 transform.position = Networking.GetOwner(gameObject).GetPosition();
 }

}
```





 



1. 오브젝트의 오너가 게임을 나갔기에, GetPosition을 하지 못하고 Udon Error가 난다
2. 오브젝트의 오너가 게임을 나가더라도, 다른 사람이 오너가 되기 때문에 Owner만 바뀔 뿐 정상작동된다

​

​

​

​

​

정답은 아래를 드래그...

정답은... 2번입니다!

​

​





 



> 
> Case2:할당되지 않은 Player를 GetPosition하면?
> 
> 
> 









이번에는 아래와 같이, VRCPlayerAPI player를 할당하지 않고 GetPosition을 받아보겠습니다. 어떻게 될까요?





 




```
private VRCPlayerApi player;
 private void Update()
 {
 transform.position = player.GetPosition();
 }
```





 



1. player가 비어 있으므로 null Error 가 난다
2. player가 없으므로 (0,0,0)으로 설정된다

​

​

​

​

​

​

​

​

정답은... 1번입니다

​

​

​

​

​

아래와 같이, player 가 비어 있으므로 null을 반환하게 되어, UdonError가 발생하게 됩니다





 




```
[UdonSharp] Assets/\_rage147/temp.cs(15,29): Udon runtime exception detected!
 An exception occurred during EXTERN to 'VRCSDKBaseVRCPlayerApi.\_\_GetPosition\_\_UnityEngineVector3'.
 Parameter Addresses: 0x00000003, 0x00000006
 
 Object reference not set to an instance of an object
```





 



​

따라서 위의 코드를 작동 가능하게 사용하려면 null이면 player를 할당해줘야 합니다





 




```
private VRCPlayerApi player;
 private void Update()
 {
 if (player == null)
 {
 player = Networking.GetOwner(gameObject);
 }
 }
```





 



아쉽게도 private VRCPlayerApi player = new VRCPlayerApi; 처럼 비어있는 VRCPlayerApi를 만들 수 없기때문에, 사용하려는 코드에서 null check를 해줘야 합니다

​

​

​

​

TMI로, 아래와 같이 optional chaining을 사용하는 방법도 있으나 ConditionalAccessExpression이 Udon에서 사용 불가능합니다

Assets/\_rage147/temp.cs(15,29): UdonSharp does not currently support node type 'ConditionalAccessExpression'





 




```
private void Update()
{
 player ??= Networking.GetOwner(gameObject);
 // Optional chaining을 사용하여 null인 경우에는 GetPosition()을 호출하지 않습니다.
 transform.position = player?.GetPosition() ?? transform.position;
}
```





 



​

​

​

대신 Null Coalescing Operator는 사용 가능하여 아래와 같이 쓸 수 있습니다





 




```
private VRCPlayerApi player;
 private void Update()
 {
 player = player ?? Networking.GetOwner(gameObject);
 transform.position = player.GetPosition();
 
 }
```





 



주의점으로는, Null Coalescing Operator은 앞의 값이 null이면 값을 계속 초기화시키므로, 위 코드에서는 Update(프레임)마다 player가 할당되게 됩니다. 따라서 반복적으로 실행되지 않는 null check에 적합하겠지요

​

​

​

​

​





 



> 
> Case3:VRCPlayerAPI에 특정 플레이어를 할당 한 뒤, 특정 플레이어가 나간다면?
> 
> 
> 









이번엔 Interact로 플레이어를 모두에게 지정한 다음, 플레이어가 할당되면 그 플레이어를 따라가게 하겠습니다

만약 오브젝트가 플레이어를 따라가다가, 플레이어가 나간다면 어떤 일이 일어날까요?





 




```
private VRCPlayerApi player;
 
 private void Update()
 {
 if (player != null)
 {
 transform.position = player.GetPosition();
 }
 }

 public override void Interact()
 {
 SendCustomNetworkEvent(NetworkEventTarget.All,"SetPlayer"+player.playerId);
 }

 private void \_SetPlayer(int \_index)
 {
 player = VRCPlayerApi.GetPlayerById(\_index);
 }
 public void SetPlayer0()
 {
 \_SetPlayer(0);
 }
 public void SetPlayer1()
 {
 \_SetPlayer(1);
 }
 public void SetPlayer2()
 {
 \_SetPlayer(2);
 }
```





 



​

​

1. 플레이어가 나가므로, player.GetPosition()에서 마지막에 있던 값으로 고정된다
2. 플레이어가 나가므로 player.GetPosition()에서 UdonError가 발생한다

​

​

​

정답은....2번입니다

​

​

​

​

아래와 같이 UdonError가 발생하게 됩니다





 




```
[UdonSharp][Unknown] Assets/\_rage147/temp.cs(17,54): VRChat client runtime Udon exception detected!
 An exception occurred during EXTERN to 'VRCSDKBaseVRCPlayerApi.\_\_GetPosition\_\_UnityEngineVector3'.
 Parameter Addresses: 0x00000003, 0x00000012
 
 Object reference not set to an instance of an object.
```





 



PlayerAPI자체는 null이 아니지만, Getposition에서 null이 발생합니다

​

​

​

​

​

​

​

​

Case1: Getowner(this.gameobject).getpositon 을 update에서 call

=⇒ GetOwner는 기존 플레이어가 나가더라도 바로 작동함

​

Case2:VRCPlayerAPI에 저장 한 뒤, 저장한 플레이어가 나가면? 

player가 나가더라도 저장한 PlayerAPI는 NotNull if(player==null)

​

Case3:VRCPlayerAPI에 저장 한 뒤 플레이어가 나가면?

 if(player.invalid()) player가 저장이 안되어 있을 경우에는 isvalid()가 Udon Error

​

Case4:invalid한 플레이어에게 Getposition을 한다면?

invalid는 false지만, Udon Error

​

​

==> PlayerAPI가 유효한지 Check하려면 null인지, valid인지 두번 check해야함

​

​

​

​





 




```
public static bool PlayerIsInWorld(VRCPlayerApi player)
{
 return player != null && player.IsValid();
}
```





 



static으로 클래스에서 선언하긴 했는데, Udon특성상 다른 함수 호출을 할 때, SendcustomEvent와 값으로 보내서 가비지가 쌓이게 된다.

static도 포함되는지는 모르겠네

​

​

​

​

​

+

static 선언





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2024-1-21-VRCPlayer의 null check/0.png)](#)








​

+

non static





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2024-1-21-VRCPlayer의 null check/1.png)](#)








​

​

static은 가비지 컬렉터가 쌓이지 않는 걸로