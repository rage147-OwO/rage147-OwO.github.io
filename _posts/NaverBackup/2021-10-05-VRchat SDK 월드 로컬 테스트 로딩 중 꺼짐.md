---
title: "VRchat SDK 월드 로컬 테스트 로딩 중 꺼짐"
date: 2021-10-05
categories:
 - VRchat
naver_url: https://blog.naver.com/rage147-owo/222527879082
---

필자는 VRchat SDK3 에서 로컬 테스트를 하는 중 꺼지는 문제가 생겼었다

![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/222527879082/458e9334ea0b.png)

로그의 스크린샷.

로딩 화면 중 꺼진다.

해결방법은

![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/222527879082/dd1a7bc3ca26.png)

SDK의 세티에서 맨 아래 VRchat Client를 들어가

Edit에서 올바른 VRchat.exe 파일을 연결 해 주면 됀다.

VRchat이 다른 디스크에 설치 돼어 있을 때 SDK는 오큘러스같은 다른 VRchat exe를 찾게 돼고

그로 인해 문제가 생긴 듯 하다.