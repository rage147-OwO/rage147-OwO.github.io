---
title: "c언어 반복문 while, do while"
categories:
 - C
---
#c언어 반복문 while, do while : 네이버 블로그







c언어 반복문입니다. 보통 중간고사 범위가 여기까지 나와요

반복문은 크게 while과 for이 있습니다.

​

while (true)

{

 printf(" ")

}

while 뒤 괄호안에 있는 값이 사실(1)이 되면 아래의 식을 반복합니다.

​




 




```
#include
main(void) {
 int i, n, sum;
 puts("정수를 입력하세요");
 scanf(" %d", &n);
 i = 1;
 sum = 0;
 while (i <= n) //입력한 수까지 1씩 올라가는 i
 {
 sum += i; //sum +=i 는 sum = sum+i, 기존의 sum에 i를 더함
 i++; //i를 1씩 올린다
 }
 printf("1부터 %d 까지의 합은 %d 입니다", n, sum);
 return 0;
 
}
```





 


위 코드는 정수를 입력받고(a) i를 1로 초기화 한 후 1(i) 부터 입력한 정수(n)까지 i를 1씩 더한것을 sum에 더하는 코드입니다. 




 




```
#include
main(void) {
 int i, n, sum;
 puts("정수를 입력하세요");
 scanf(" %d", &n);
 i = 0;
 sum = 0;
 while (i <= n)
 {
 sum += i;
 i = i + 2;;
 }
 printf("0부터 %d까지 짝수의 합은 %d입니다 ", n, sum);
 return 0;
 
}
```





 


다음은 0부터 입력받은 n까지에 있는 짝수를 더하는 코드입니다.

i는 0이였지만 i=i+2에 의해 반복시 2씩 올라가게 됩니다

​




 




```
#include
main(void) {
 int i, n, sum;
 puts("5개의 정수를 입력하세요");
 i = 1;
 sum = 0;
 while (i <= 5)
 {
 scanf("%d", &n);
 sum =sum+ n;
 i++;
 }
 printf(" 5개의 합은 %d입니다 ", sum);
 return 0;
 
}
```





 


다음은 입력받은 정수 5개를 더하는 코드입니다.

scanf도 반복 안에 넣음으로써 입력도 반복을 시킬 수 있습니다.

​




 




```
#include
main(void) {
 int i, n, sum,average;
 n=0,
 sum = 0;
 i = 0;
 while (i>=0) //i가 0보다 크면 종료한다
 {
 puts("성적을 입력하세요");
 scanf("%d", &i); //i를 입력받는다
 sum += i; //입력받은 i를 sum에 더한다
 n++; //총 몇번 반복이 되었는지를 센다
 } //반복에서 나가기 위해서는 마이너스 값을 입력한다
 sum = sum - i; //마지막에 저장된 i값은 마이너스므로 마지막 더한값을 뺀다
 n--; //이또한 같게 마지막에 반복된것은 마이너스를 더한 것이므로 반복으로 셀 수 없다
 average = sum / n;
 printf("학생의 수 %d\n총 성적의 합계%d\n성적의 평균은 %d ",n,sum, average);
 return 0;
 
}
```





 


​




 




```
#include
#include //INT\_MAX를 쓸 수 있게 하는 헤더
main(void) {
 int num, min\_value = INT\_MAX;
 puts("정수를 입력하세요\n종료는 컨트롤z3엔터 3번");
 while (scanf("%d",#) != EOF) //num을 입력받는다,!=EOF는 컨트롤 z가 아니면 실행한다라는 뜻
 {
 if (num < min\_value) //입력받은 num이 min\_value보다 작으면
 min\_value = num; //num을 min\_value에 넣는다
 }
 printf("최소값은 %d ",min\_value);
 return 0;
 
}
```





 


​

​

아래의 예제는 랜덤한 숫자를 만들어 숫자를 맞추는 코드이다




 




```
#include
#include
#include
int main() {
 int i = 0;
 int o;
 srand(time(NULL));
 o = rand() % 45 + 1; //45까지의 랜덤한 수를 o로 지정한다


 do
 {
 puts("추측 숫자를 입력하세요");
 scanf(" %d", &i);
 if (o < i)
 puts("추측 숫자보다 작습니다");
 if (o > i)
 puts("추측 숫자보다 큽니다");
 } while (i != o);

 printf("맞췄습니다 숫자는 %d 입니다\n", i);
}
```





 


do while은 일다나 실행하고 조건에 참이면 계속 반복하는 반복문이다.

위 코드에서는 45까지 랜덤한 수 o와 입력한 수 i가 같지 않으면 반복하게 되어 있다

​

고로 o와 i가 같게 되면 반복이 끝나고 i를 출력하게 된다

​




 

