---
title: "python Serial CPU 100% 사용중일때"
date: 2024-07-03
categories:
 - AI
naver_url: https://blog.naver.com/rage147-owo/223500050317
---

회사에서 프로그램 개발 중, 내가 담당한 IO 로직쪽에서 CPU 100%를 사용하는 현상이 발견되었다.

어딘지 찾아보니, python Serial을 프로세서로 분리했는데, 이 프로세스에서 만들어진 read thread가 문제였다.

```
while True:
    if(ser.in_waiting > 0):
        data = ser.read()
        print(data)
```

위와 같은 코드를 사용하면 serial에서 in\_waiting을 계속 접근하여 IO와 thread 간 충돌이 나는 듯 하다

![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/223500050317/5cf2d2808c66.png)

위 코드만 돌리는데 CPU코어를 꽉채우는 마법

아래와 같은 코드로 작성하면 해결된다

```
def read_thread():
    while True:
        data = ser.read()
        print(data)
        time.sleep(1)
```