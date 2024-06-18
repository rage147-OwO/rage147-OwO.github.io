title: "Docker 사용해보기(Windows 10)"
categories:
 - personalproject
---
#Docker 사용해보기(Windows 10) : 네이버 블로그








> 
> 들어가며
> 
> 
> 그렇게 핫하다는 Docker, 지금 사용해보았다
> 
> 
> 









최근 한 지인이 Docker가 그렇게 편하다 하여 한번 사용해보았다

​

[Docker는 가상화 플랫폼인데, 기존은 운영체제를 가상화시켰다고 하면, Docker는 프로그램을 가상화하며, 호스트와는 완전히 분리된 환경을 사용하며, 충돌을 내지 않는다](https://docs.docker.com/get-started/overview/)





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-5-3-Docker 사용해보기(Windows 10)/0.png)](#)








GCP에서 우분투를 사용하면서도, 서로 다른 환경이기에 초기 설정을 하기 귀찮았는데, 이참에 Docker를 사용해보기로 한다

​

​

​





 



> 
> 준비하기
> 
> 
> DockerDesktop 설치 & 이미지 준비
> 
> 
> 









먼저 [dockerDescktop](https://www.docker.com/products/docker-desktop/)을 설치한다

​

튜토리얼 [리포지토리](https://github.com/docker/getting-started)를 받은 뒤

​

리포지토리의 app/하위에

Dockerfile이라는 이름의 파일을 생성한 뒤 아래 코드를 넣는다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-5-3-Docker 사용해보기(Windows 10)/1.png)](#)









```
# syntax=docker/dockerfile:1
 
FROM node:18-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```





 



​

​





 



> 
> 도커 이미지 빌드하기
> 
> 
> 









docker Desktop을 실행 한 뒤, cmd에서 docker build -t <이미지이름> <Dockerfile 경로>를 입력한다

docker build -t myimage C:\Users\User\Documents\GitHub\getting-started\app

​

빌드가 완료되면





 




```
docker images
```





 



를 실행해 현재 이미지를 확인할 수 있다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-5-3-Docker 사용해보기(Windows 10)/2.png)](#)








​

​





 



> 
> 이미지로 컨테이너 생성하고 실행하기
> 
> 
> 









docker run --name <컨테이너이름> -p <호스트포트>:<컨테이너포트> <이미지이름>





 




```
docker run --name mycontainer -p 8080:80 myimage
```





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-5-3-Docker 사용해보기(Windows 10)/3.png)](#)








<http://localhost:8080/>에서 로딩이 되지 않는다면, 방화벽의 포트포워딩 문제일 수 있다.

​

필자는 컨테이너틀 중지한 뒤 rm으로 삭제한 뒤 컨테이너포트를 변경했다

​

중지 : docker stop mycontainer

제거 : docker rm mycontainer

​





 




```
docker run --name mycontainer -p 8080:3000 myimage
```





 



​

getting-started 앱이 실행되었다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-5-3-Docker 사용해보기(Windows 10)/4.png)](#)








​

​

일반적으로 하나의 이미지에 하나의 컨테이너를 사용하나

[도커 컴포즈(Docker Compose)](https://docs.docker.com/get-started/08_using_compose/)를 사용해서, 여러 개의 컨테이너를 정의하고, 실행하고, 관리 할 수 있다.

​

​