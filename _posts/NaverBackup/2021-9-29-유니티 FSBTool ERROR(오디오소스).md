title: "유니티 FSBTool ERROR(오디오소스)"
categories:
 - VRCHAT
---
#유니티 FSBTool ERROR(오디오소스) : 네이버 블로그








오디오 소스를 불러 올 때 FSBTool오류가 날 때가 있다.

​

Errors during import of AudioClip Assets/Sounds/SomeSound.mp3:

FSBTool ERROR: Could not find encoder library 'libvorbis.dll', please copy it from the FMOD SDK to the application directory.

FSBTool ERROR: Encoder initialization failed.

FSBTool ERROR: Encoder initialization failed.





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-29-유니티 FSBTool ERROR(오디오소스)/0.png)](#)








​

​

​

​

​

​

​

FSBTool이 윈도우 디펜더에서 걸려 실행이 안돼는 것이다.

아래 윈도우 보안 탭 설정을 들어가





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-29-유니티 FSBTool ERROR(오디오소스)/1.png)](#)








​

​

​

​

제외 사항 추가를 눌러 폴더 를 선택하고 유니티 폴더 위치를 찾자.





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2021-9-29-유니티 FSBTool ERROR(오디오소스)/2.png)](#)








​