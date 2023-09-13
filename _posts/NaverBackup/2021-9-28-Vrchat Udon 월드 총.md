---
title: "Vrchat Udon 월드 총"
categories:
 - UDONSHARPexample
---
#Vrchat Udon 월드 총 : 네이버 블로그








디스코드 rage147#2898

우동 관심있는분 친추 주세요!!

아니면 서버 들어오세용~~

<https://discord.gg/E8rF9uTggA>

​

​

​





 





---





 



오늘 소개할 것은 

맞으면 텔레포트 하는 총입니다

<https://booth.pm/ja/items/2683757>

총의 모델은 위 부스에서 가져왔습니다!!

​

​





 



**첨부파일**

TeleportGun.unitypackage

[파일 다운로드](https://download.blog.naver.com/open/099c15a6bdeded311df29eae91710f70d0807f9f72/YR0ba48RDipTiY_UTWtfzM40y8pvKGiqGZp1v_tI4-2i4LEdian-0QSMpuDgBBS_B0kGrhvgBJ4VXqF-SSxvTQ/TeleportGun.unitypackage)




 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-28-Vrchat Udon 월드 총/0.png)](#)








프리펩 안에는 gun이 메인으로 있고

BulletParticle 

AimCam

gun model

Gunsound

네가지 하위 오브젝트가 있습니다

​

gun은 플레이어가 들 수 있고 마우스 클릭이나 VR트리거를 당기면 파티클을 활성화시키는 기능을 합니다

AimCam은 총을 들면 에임 카메라가 켜지고 화면을 보여주는 기능을 합니다

gun model은 총의 3d 모델입니다

Gunsound는 발사음 소리 소스입니다

​

​

​

​

먼저 세부적인 기능 맞으면 텔레포트를 하게 돼는 BulletParticle 부터 보겠습니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-28-Vrchat Udon 월드 총/1.png)](#)








일단 파티클의 Collision을 키고

Collides with에서 Player와 PlayerLocal을 선택합니다

​

이것은 맞으면 반응하는 파티클과 같은 원리입니다.

<https://gall.dcinside.com/mgallery/board/view/?id=vr&no=85714>





 



[![](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fwrite.dcinside.com%2Fviewimage.php%3Fid%3Dvr%26no%3D24b0d769e1d32ca73cee87fa11d02831d3049d5484b72b456f01af270de120e279a76081e56374bf6d56d76d488e861d9f3ab9eef1a85fd063a4c8%22&type=ff120)](https://gall.dcinside.com/mgallery/board/view/?id=vr&no=85714)
[**[강좌]플레이어에게 맞으면 반응하는 파티클 만들기 - VRChat 갤러리**
응용은 알아서 하면 됨.너네들이 그렇게 궁금해하던 데스건의 원리이기도 하다.하지만 이 기술이 풀린다고 해서 데스건 만들 놈들은 원래부터 그럴놈들(핵을쓰든 뭘쓰든 데스건쏠 떡잎놈들)이라 생각되고, 너희들이 좀 더 멋진


gall.dcinside.com](https://gall.dcinside.com/mgallery/board/view/?id=vr&no=85714)




 



위의 링크에서는 파티클이 플레이어와 반응하면 새로운 파티클을 생성하지만

​

제가 필요했던것은 플레이어가 부딫히면 특정 이벤트를 실행하는 것이였습니다

그러므로 사진 아래처럼

Send Collision Messages를 킵니다

이로 인해 플레이어가 부딪히면 특정 이벤트가 실행됩니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-28-Vrchat Udon 월드 총/2.png)](#)








파티클 시스템 내에 있는 소스 코드입니다





 




```
using UdonSharp;
using UnityEngine;
using VRC.SDKBase;
using VRC.Udon;
using UnityEngine.UI;

public class particle : UdonSharpBehaviour
{
 public Vector3 O\_Vector3;//맞으면 텔레포트 될 위치
 
 Quaternion Quater; //회전각입니다. 기본으로 설정합니다

 void Start()
 {
 }
 public override void OnPlayerParticleCollision(VRCPlayerApi player) //파티클에 아까 설정한 플레이어가 맞으면 실행되는 이벤트입니다
 {
 //위에서 선언된 VRCPlayerApi player는 부딪힌 플레이어를 의미합니다.
 player.TeleportTo(O\_Vector3, Quater);//텔레포트를 보내줍시다
 }

}
```





 



엄청 간단한 코드입니다.

저는 많이 헤맸었는데 

OnCollisionEnter와 OnTriggerEnter를 처음에 써보다가 작동을 안하기에 삽질을 하다가 찾게 되었습니다

​

어쨋거나 간단한 코드지요?

​

​

​

다음은 총인 gun입니다

먼저 컴포넌트부터 보겠습니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-28-Vrchat Udon 월드 총/3.png)](#)








VRC Pickup을 추가해 손으로 집을 수 있게 했습니다

아래는 Udon 스크립트

그 아래는 오브젝트의 싱크를 (글로벌오브젝트)설정해

다른 플레이어가 물건을 이동시켜도 같이 움직이게끔 합니다

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-28-Vrchat Udon 월드 총/4.png)](#)








Pickup인지 Syne문제인지 모르겠지만

Udon 스크립트에서 Manual로 하려니깐 오류가 나더라고요.

메뉴얼로도 pickup을 설정할수 있을거같긴 한데 귀찮으니 그냥 Continuous를 사용했습니다

​

​

​

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-28-Vrchat Udon 월드 총/5.png)](#)








gun안의 코드입니다.

하나씩 보겠습니다

gun 코드의 기능을 크게 나누자면

잡으면 에임 화면 키기

플레이어가 클릭이나 VR트리거를 누르면 총을 쏘기

총알이 날라가는 동안 총을 못쏘게 하기

컴퓨터인 경우 총을 집을 때 자동으로 총을 쏘는 경우가 생김. 이를 방지

​

이렇게 나눌 수 있습니다

​

아래는 변수들입니다





 




```
public float ReloadTime = 0.2f; //한발을 쏜 후 기다리는 시간입니다. 너무 짧으면 연타할때 기관총처럼 나갑니다

 bool GunShotCheck;//update에서 총을 쏘는지를 검사합니다
 bool GunShotCheckOnce;//총을 쏠때 한번 해야하느 과정을 했는지 검사힙니다
 bool CheckEnd;//총을 쏘는 과정이 끝났는지 검사합니다
 public GameObject Gun;//Gun은 파티클 게임 오브젝트입니다
 float time;//시간을 저장할 변수입니다
 public AudioSource gunsound; //총을 쏠때 나오는 사운드입니다
 int Computer = 0;//컴퓨터일때 사용하는 과정입니다
 public GameObject Aim; //에임 카메라입니다
```





 



먼저 잡으면 에임 화면 키기부터 보겠습니다





 




```
public override void OnPickup() //손으로 들면
 {
 Aim.SetActive(true); //Aim게임 오브젝트를 활성화합니다
 }
```





 



Aim은 카메라가 있고 카메라의 화면이 있습니다. 손으로 잡음으로 에임을 활성화합니다

​

잡으면 에임 화면 키기

플레이어가 클릭이나 VR트리거를 누르면 총을 쏘기

총알이 날라가는 동안 총을 못쏘게 하기

컴퓨터인 경우 총을 집을 때 자동으로 총을 쏘는 경우가 생김. 이를 방지

​

하나 끝

​





 




```
public override void OnPickupUseDown()//이 이벤트는 물건을 든 후 마우스를 누르면 실행됩니다
 { //이 물건을 집은 후 작동을 하면 이 이벤트가 실행됩니다
 //컴퓨터인 경우 물건을 집으면 바로 쏴지는 현상이 있습니다. 이를 방지하기 위해 컴퓨터는 두번 이상 작동해야 총을 쏠 수 있게 합니다
 if (Networking.LocalPlayer.IsUserInVR() == false) //vr이 아니면
 {
 if (Computer > 1)//Computer는 아래 else에서 1 증가합니다. 즉 2번이상 작동해야 진짜 총을 쏠 수 있습니다. 그 전은 총을 잡을 때 총알이 발사되는 현상을 방지합니다
 {
 if (CheckEnd)
 {
 CheckEnd = false;//총을 쏘는 중임을 의미합니다.
 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "GunShot");
 //모든 플레이어에게 GunShot라는 기능을 실행시킵니다
 
 }
 }
 else //작동이 2번 이하면 Computer를 1 올려 위 코드를 실행하게 합니다
 Computer++;
 }
 else //vr이면
 {
 if (CheckEnd)//
 {
 CheckEnd = false;//총을 쏘는 중임을 의미합니다.
 SendCustomNetworkEvent(VRC.Udon.Common.Interfaces.NetworkEventTarget.All, "GunShot");
 //모든 플레이어에게 GunShot라는 기능을 실행시킵니다
 }
 }
```





 



플레이어가 클릭이나 VR트리거를 누르면 총을 쏘기

총알이 날라가는 동안 총을 못쏘게 하기

컴퓨터인 경우 총을 집을 때 자동으로 총을 쏘는 경우가 생김. 이를 방지

​

​

​

​

​

​





 




```
//위에서 실행된 GunShot입니다
 public void GunShot()
 {
 Gun.SetActive(true); //파티클을 활성화시킵니다
 GunShotCheck = true; //총을 쏘는 것을 검사하는 GunShotCheck를 참으로 둡니다
 GunShotCheckOnce = true; //총을 쏠 때 한번 하는 과정을 참으로 둡니다
 
 }
```





 



플레이어가 클릭이나 VR트리거를 누르면 총을 쏘기

총알이 날라가는 동안 총을 못쏘게 하기

​

​

​

​

​

​

​





 




```
//update에서 시간을 측정합니다

 private void Update()
 {
 
 if (GunShotCheck) //총을 쏘는지 검사
 {
 if (GunShotCheckOnce) 
 {
 gunsound.Play(); //총 소리 내기
 time = Time.time; //시간 기준을 잡기
 GunShotCheckOnce = false; //한번만 실행

 }

 if (time + ReloadTime < Time.time) { 
 Gun.SetActive(false); //파티클을 끄기
 GunShotCheck = false; //더이상 update에서 총을 발사하지 않음
 CheckEnd = true ; //총 발사가 끝났음을 알림
 }
 }
 }
```





 



총알이 날라가는 동안 총을 못쏘게 하기

​

​

이렇게 코드에 대한 설명이 끝났습니다

​

하나 더 설명하면 카메라입니다

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-28-Vrchat Udon 월드 총/6.png)](#)








조준 화면을 만드는 방법

카메라를 추가 한 후 Assets에 빈 메테리얼을 만듭니다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-28-Vrchat Udon 월드 총/7.png)](#)








타겟 텍스쳐에 넣으면 이 텍스쳐가 화면이 됩니다.

​

​

​

ps. 처음에는 

물건일 집고 입력을 받을 때

​

public override void InputUse(bool value, UdonInputEventArgs args)

​

InputUse를 썼었습니다

​

그런데 이는 물건을 집고 입력을 받는 것이 아닌 모든 플레이어에게 입력을 받는 것이였습니다

즉 물건을 잡지 않아도 총을 쏠 수 있었습니다;;

​

이후 OnPickupUseDown()을 사용하니 해결되었습니다.





 

