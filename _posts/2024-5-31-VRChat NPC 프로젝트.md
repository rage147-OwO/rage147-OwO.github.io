title: "VRChat NPC 프로젝트"
categories:
 - VRCHAT
---
#VRChat NPC 프로젝트 : 네이버 블로그








최근 VRChat으로 하고 있는 프로젝트

​

NPC 만들기. 프로젝트 진행중에 문서화 겸 저장용으로 올려둔다

언제쯤 완성하려나

​

​

컨셉 : 방랑시인 레이지

방랑시인은 VRChat 내에서 플레이어들의 모험과 이야기를 감지하고 관련된 이야기를 제공하는 역할을 합니다. 이 NPC는 플레이어의 외관과 활동을 분석하여 적절한 이야기를 생성하며, TTS(Text-to-Speech) 기술을 활용하여 플레이어에게 전달합니다.

시인은 주변 플레이어들의 존재를 감지하고, 특정 플레이어를 발견하면 그에게 다가가 상호작용합니다. 이때, 플레이어들의 대화를 듣고 분석하여 관련된 이야기를 만들어냅니다. 또한, 플레이어가 "레이지"와 같은 닉네임을 언급할 경우 이를 감지하고 해당 플레이어에게 반응합니다.

생성된 이야기는 GPT API를 활용하여 자연스러운 대화로 구성되며, 이를 TTS 기술을 통해 플레이어에게 음성으로 전달합니다. 플레이어는 이야기를 듣고 싶다면 "방랑시인님 이야기를 들려주세요"와 같은 요청을 하면 됩니다.

방랑시인은 게임 내에서 플레이어들에게 다양한 이야기와 경험을 제공하여 게임의 재미를 증진시키고, 플레이어들과의 상호작용을 활성화하는 역할을 합니다. 이를 통해 VRChat 경험을 더욱 풍부하고 유익하게 만들어줍니다.

​​

​





 




```
VRChat PC에서 할 수 있는 행동
1. 이동/점프/앉기/엎드리기
2. 채팅 입력
3. 오디오 STT
4. GPT API를 사용한 대화
5. TTS를 사용한 대답 
6. 플레이어 nameplate 감지


기능
- 다른 플레이어들의 대화 내용을 듣고 대답 할 수 있음
- STT으로 나의 닉네임인 "레이지"를 부르면 시리처럼 gpt api로 TTS 대답하는 기능
- 가까운 플레이어가 없을 경우 플레이어를 찾고 접근하는 기능
- 플레이어의 외관을 보고 관련 시를 작성
- 현재 대화와 상황, 보이는 것들을 인식하여 시 작성
```





 



​

​

오디오 인식

Google, ETRI STT를 사용중인데 인식률이 낮다

대화 전용 AI를 찾아야 할듯?





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2024-5-31-VRChat NPC 프로젝트/0.png)](#)








​

OSC로 채팅 표시 기능 구현 완

​

​

​

시각적인 요소로는 NamePlate를 인식한다.

이후로는 물체, 플레이어 외관 등을 인식해야 함





 







 



​

​

​

프롬프트 컨셉은 이런 느낌:

=>VRChat에서 고양이 아바타를 한 사람이 있어. 그 사람에 대한 140자 이하 시나 이야기를 재미있게 만들어봐

=>

어느 날 VRChat에서 만난 고양이 아바타를 한 친구, '퍼시'는 털부터 발끝까지 끼리끼리 하고 있었어. 그래서 그의 닉네임은 '퍼시 끼끼'로 알려졌지. 그는 마을에서 유명한 고양이 마녀라고 자처하며, "냥이 주문"으로 누구나 행복해져보라고 소리쳤어. 그런데 한번 그가 물었다, "고양이의 귀는 마법이야, 아니면 단순히 귀가 헝클어진 털 더미일까?"

​

​

방랑시인 아바타부터 만들어야겠구만

​

개인적으론 스카이림 바드 느낌에 한국적 특색을 넣고 싶음

찾아보니 조선 후기에 전기수라는 직업이 있었다네 

​

타령이나 탈춤 NPC도 괜찮을 것 같기도 하고...?

이것이 K-NPC? zzzzㅋㅋㅋㅋ





 




[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2024-5-31-VRChat NPC 프로젝트/1.png)](#)


[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2024-5-31-VRChat NPC 프로젝트/2.png)](#)




 



​

​

스카이림에서 구현된 gpt연동 npc​

[https://youtu.be/vWMLVZF3pGc?si=zlUz0yYrPcZ1](https://youtu.be/vWMLVZF3pGc?si=zlUz0yYrPcZ1COsl)





 











[COsl](https://youtu.be/vWMLVZF3pGc?si=zlUz0yYrPcZ1COsl)