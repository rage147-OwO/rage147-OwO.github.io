---
title: "AVD Pixel\_3\_API\_30 에뮬레이터 에러 해결법"
categories:
 - memo
---








안녕하세요.

이번 포스팅에서는 안드로이드 스튜디오에서 AVD(Android Virtual Device)를 실행할 때 발생하는 "Error while waiting for device: The emulator process for AVD Pixel\_3\_API\_30 has terminated" 에러에 대해서 알아보겠습니다.

이 에러는 AVD를 실행하려고 시도했지만, 에뮬레이터 프로세스가 예기치 않게 종료되어 발생합니다. 대부분의 경우 이 문제는 AVD가 충돌하거나 더 이상 작동하지 않는 상태가 되어 발생합니다.

해결하기 위해서는 몇 가지 단계를 따라야 합니다. 먼저, 안드로이드 스튜디오에서 AVD를 다시 시작하고, 불필요한 프로그램을 모두 종료하고, 컴퓨터를 다시 시작해 볼 수 있습니다. 만약 이러한 단계를 수행했는데도 문제가 해결되지 않는다면, AVD를 다시 생성하거나 이미지를 변경하여 해결할 수 있습니다.

AVD를 다시 생성하는 방법은 다음과 같습니다.

​

1. 안드로이드 스튜디오를 실행합니다.
2. AVD Manager를 엽니다.
3. Create Virtual Device를 클릭합니다.
4. 원하는 디바이스를 선택하고, 필요한 시스템 이미지를 선택합니다.
5. AVD 이름을 지정하고, Finish 버튼을 클릭합니다.

이러한 단계를 수행한 후에도 문제가 해결되지 않으면, 그래픽을 변경하여 해결할 수 있습니다. 이 경우에는 다음과 같은 단계를 따릅니다.

​

​

1. AVD Manager에서 수정하려는 AVD를 선택합니다.
2. Edit 버튼을 클릭합니다.
3. Show Advanced Settings를 클릭합니다.
4. Emulated Performance 섹션으로 이동합니다.
5. Graphics 옵션을 변경합니다. (예 : Software - GLES 2.0)
6. Finish 버튼을 클릭합니다.

이제 다시 AVD를 시작하면 정상적으로 실행되어 에러가 발생하지 않을 것입니다.

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-3-8-AVD Pixel_3_API_30 에뮬레이터 에러 해결법/0.png)](#)








​

그래픽 드라이버가 최신 버전이 아니거나 OpenGL ES 에뮬레이션 초기화가 실패한 경우 에러가 뜹니다

​

그 외에도 다양한 이유로 에러가 뜰 수 있으니 로그를 참고하세요

로그의 경로는 

C:\Users\사용자\AppData\Local\Google\AndroidStudio버전\log에 

log.txt.입니다

​





 

