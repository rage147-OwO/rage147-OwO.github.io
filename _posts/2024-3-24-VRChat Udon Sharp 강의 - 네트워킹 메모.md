title: "VRChat Udon Sharp 강의 - 네트워킹 메모"
categories:
 - UDONSHARPcourse
---
#VRChat Udon Sharp 강의 - 네트워킹 메모 : 네이버 블로그








여~ 알아서들 보라고

​

<https://youtu.be/J_aEljaznho>





 











​

<https://blog.naver.com/rage147-owo/222990230516>

​

​

​

​

쉬운이론

1. 네트워크 오너, 오너쉽 개념 0:00

​

​

2. 샌드커스텀네트워크이벤트 9:21

​

​

3. 싱크변수

오너일경우에만 Set할 수 있다

​

​

4. 싱크모드

None : 로컬로만 작동, OntriggerEnter같은건 된다. SendCustomNetworkEvent, Sync변수 안된다

Continuous : 싱크변수 자동 동기됨, SendCustomNetworkEvent된다

manual : 싱크변수 수동 동기, SendCustomNetworkEvent된다

​

​

 [UdonSynced(),FieldChangeCallback(nameof(money)),SerializeField]private float \_money;

 public float money

 {

 get => \_money;

 set

 {

 if (value != \_money)

 {

 if (Networking.IsOwner(this.gameObject))

 {

 \_money = value;

 RequestSerialization();

 }

 else

 {

 \_money = value;

 }

 playerManager.MoneyChanged();

 }

 }

 }

​

​

5. 컴포넌트 42:00

VRCObjectSync

VRCInstantiate

VRCObjectPool

​

​

public void Return(int i)

{

if (Networking.IsOwner(Pool.Pool[i]))

{

Pool.Pool[i].GetComponent<VRCObjectSync>().Respawn();

}

​

if (Networking.IsOwner(this.gameObject))

{

if (!Networking.IsOwner(Pool.Pool[i]))

{

Networking.SetOwner(Networking.LocalPlayer, Pool.Pool[i]);

}

​

Pool.Pool[i].GetComponent<VRCObjectSync>().Respawn();

Pool.Return(Pool.Pool[i]);

}

}

​

휴식 1시 55분 까지

​

​

​

​

​

6. 디버깅 1:10:00

​

​

7.PlayerAPI 1:18:00

​

​

​

​

8.Networking 1:35:00

​

​

​

9. 예제

​

예제 1번 오브젝트 픽업 Pool로 스폰 Return

스폰->인터렉트하면 SendCustomNetworkEvent All 스폰

리스폰->인덱스로 SendCustomNetworkEvent All, ObjectSync.respawn Reuturn

​

​

​

예제 2번

몬스터에서 인식, 오너에서 OnTrigger한다음 무기의 Damege계산, 몬스터의 HP를 빼고 RequestSerialization

​

예제 3번

몬스터 위치 싱크하기 1:46:00

0.4초마다 동기

목표 Position

현재 Position

​

​

​

예제4번 

플레이어 특정하기 

<https://github.com/rage147-OwO/PlayerApiObjectPool>

1. SendCustomNetworkEvent 인덱스로 하기 getplayerid

2. getplayers한다음 정렬하기

3. 플레이어 할당 오브젝트 사용하기

​

할당을 한 다음에, 오브젝트의 오너를 사용함

​

​

​

특정 플레이어 앞에 오브젝트 스폰

​

​

​

​

​

​

using System;

using UdonSharp;

using UnityEngine;

using UnityEngine.UI;

using VRC.SDK3.Components;

using VRC.SDKBase;

using VRC.Udon;

using VRC.Udon.Common.Interfaces;

​

[UdonBehaviourSyncMode((BehaviourSyncMode.NoVariableSync))]

[RequireComponent(typeof(VRCObjectPool))]

public class PlayerManager : UdonSharpBehaviour

{

 [HideInInspector] public VRCObjectPool pool;

 [HideInInspector] public PlayerData localPlayer;

 [HideInInspector] public PlayerData[] playerDataArray;

 public WeaponManager weaponManager;

 public GameManager gamaManager;

 public Text UdonChipsText;

 

 

 private int[] setOwnerPlayerQueue = new int[GameManager.MaxWorldPlayer]; 

 private int queueFront = 0;

 private int queueRear = -1;

 private int queueCount = 0;

 

 //플레이어 리스트 중 money가 바뀜

 public void MoneyChanged()

 {

 Debug.Log("rage147 : PlayerManager : MoneyChanged");

 UdonChipsText.text = "";

 //모든 플레이어의 UdonChipsText를 갱신

 for (int i = 0; i < playerDataArray.Length; i++)

 {

 if (playerDataArray[i].gameObject.activeInHierarchy)

 {

 UdonChipsText.text += Networking.GetOwner(playerDataArray[i].gameObject).displayName + " : " + playerDataArray[i].money.ToString() + "\n"; 

 }

 }

 }

 

 bool LocalIndexSetted = false;

 [HideInInspector] public byte LocalIndex

 {

 get=>\_localIndex;

 set

 {

 if (!LocalIndexSetted)

 {

 LocalIndexSetted = true;

 }

 \_localIndex=value;

 localPlayer=playerDataArray[\_localIndex];

 Debug.Log("PlayerManager: LocalIndex set to "+value);

 

 gamaManager.GameStart();

 

 //playermanagerStart

 

 }

 }

 

​

 [FieldChangeCallback(nameof(LocalIndex))]private byte \_localIndex;

 public void RankUp()

 {

 Debug.Log("rage147 : PlayerManager : RankUp");

 localPlayer.rank++;

 }

 private void Start()

 {

 pool=GetComponent<VRCObjectPool>();

 playerDataArray=new PlayerData[pool.Pool.Length];

 for (int i = 0; i < playerDataArray.Length; i++)

 {

 playerDataArray[i]=pool.Pool[i].GetComponent<PlayerData>();

 }

 //SendCustomEventDelayedSeconds(nameof(checkLocalIndexSetted),1f);

 }

​

 public void checkLocalIndexSetted()

 {

 if(!LocalIndexSetted)

 {

 SendCustomNetworkEvent(NetworkEventTarget.Owner, nameof(ReSetOwner));

 SendCustomEventDelayedSeconds(nameof(checkLocalIndexSetted),1f);

 }

 }

 

 private void EnqueuePlayer(int playerId)

 {

 queueRear = (queueRear + 1) % setOwnerPlayerQueue.Length;

 setOwnerPlayerQueue[queueRear] = playerId;

 queueCount++;

 }

​

 private int DequeuePlayer()

 {

 int playerId = setOwnerPlayerQueue[queueFront];

 queueFront = (queueFront + 1) % setOwnerPlayerQueue.Length;

 queueCount--;

 return playerId;

 }

 

 

 public override void OnPlayerJoined(VRCPlayerApi player)

 {

 if (Networking.IsMaster)

 {

 if (player.isLocal)

 {

 pool.TryToSpawn();

 LocalIndex = 0;

 }

 else

 {

 EnqueuePlayer(player.playerId);

 SendCustomEventDelayedSeconds(nameof(SetOwnership), 10f);

 }

 }

 }

​

​

 public void SetOwnership()

 {

 if (queueCount > 0)

 {

 int playerId = DequeuePlayer();

 VRCPlayerApi player = VRCPlayerApi.GetPlayerById(playerId);

 if (player != null && player.IsValid())

 {

 Networking.SetOwner(player, pool.TryToSpawn());

 }

 }

 }

 

 

​

 public override void OnPlayerLeft(VRCPlayerApi player)

 {

 if (Networking.IsMaster)

 {

 for (int i = 0; i < pool.Pool.Length; i++)

 {

 if ((LocalIndex != i) && (pool.Pool[i].activeInHierarchy) && (Networking.IsOwner(pool.Pool[i].gameObject)))

 {

 pool.Return(pool.Pool[i].gameObject);

 break;

 }

 }

 }

 }

​

 public void ReSetOwner()

 {

 Debug.Log("rage147 : PlayerManager : ReSetOwner");

 foreach (var playerData in pool.Pool)

 {

 if (playerData.activeInHierarchy)

 {

 Networking.SetOwner(Networking.GetOwner(playerData.gameObject),playerData.gameObject);

 break;

 }

 }

 }

}

​

4. Q누르면 오브젝트 생성하는거(플레이어 앞에)

​

​

​

10. 최적화

In 200kb/s

Out 50kb/s

각 우동비헤이비어마다 가지고 있는 싱크량이 있다<< 얘를 줄이는게 목표

​

우동싱크를 줄이는 방법

우동싱크 줄인다

0~255이하인거 byte사용한다

싱크타이밍 최소로

​

​

샌드커스텀네트워크이벤트

인덱스로 해결할수있으면 인덱스로

이름으로 보냄byte 이름은 가능하면 짧게

​

셋오너 최소화

​

​

​

최적화 중에서 가장 빠른 싱크 방법은(속도순)

시간으로 싱크<byte 싱크 manual, 샌드커스텀네트워크이벤트< objectsync&objectpool< 셋오너

​

​

항상 네트워크는 보장이 안된다

​

그나마 샌드커스텀네트워크이벤트

​

​

[udonsynced]byte number

​

number = 100

requestserialzation()

sendcustomnetwormevent(show);

​

​

최적화 <-- 시간

네트워크 

​

​

오브젝트 싱크 컴포넌트 <--컨티뉴어스라 무거움

메쉬를 바꿈

​

​

​

​