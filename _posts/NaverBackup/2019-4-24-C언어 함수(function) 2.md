---
title: "C언어 함수(function) 2"
categories:
 - C
---







c언어의 함수는 기본적으로

반환 자료형(void, int, double...) 함수이름 인수목록 {함수몸체} 의 구조로 구성된다.

​

함수는 사용자 정의 함수와 라이브러리 함수가 있는데

라이브러리 함수는 printf나 scanf처럼 헤더 파일에 정의되어있는 함수이다.

​

오늘 다루는 함수는 사용자 정의 함수이다.

사용자 정의 함수를 쓰는 이유는

1. 불필요한 중복 코드를 줄일 수 있다.

2. 체계적이고 간결하게 할 수 있다.

3. 함수 내의 변수를 선언해 변수 간의 중복을 피할 수 있다.

​

아래 예제들을 보자




 




```
#include
void happy\_birthday(){
 printf("생일축하합니다\n");
}
int main() {
 happy\_birthday(); //void는 함수()형임을 기억하자
 happy\_birthday();
 printf("사랑하는 학생의 ");
 happy\_birthday();
 return 0;
}
```





 


void happy\_birthday()는 입력(전달인자)가 없고 반환도 없는 함수이다.

여기서 반환은 return 값이다.

​

즉 printf로 인해 출력된다 해도 반환은 없다.

입력과 반환의 의도에 따라 자료형을 적절히 선택하자.

​




 




```
#include
int add(int x, int y){
 return x + y;
}
int main() {
 int x, y;
 scanf("%d%d", &x, &y);
 printf("%d", add(x, y));
 return 0;
}
```





 


add라는 함수는 add( x ,y )형태로 입력받아

x+y를 반환하는 함수이다.

​

즉 x+y는 add(x,y)와 같다.

​




 




```
#include
int fact(int n) {
 int sum = 1;
 for (int i = 1; i <= n; i++)
 {
 sum \*=i;
 }
 return sum;
}

int main() {
 int a;
 scanf("%d", &a);
 printf("%d", fact(a));
 return 0;
}
```





 


fact함수는 입력받은 int형 n의 팩토리얼을 int형 sum으로 반환하는 함수이다.

​

함수를 적절히 사용하기 위해서는 함수의 기능이 무엇인지, 무엇을 반환하는지 생각하는 것이 중요하다

​




 




```
#include
char op(); //함수 선언만 하고 내용은 아래에 적는다(함수원형)
double ch(char o);
int main() {
 double result;
 printf("%f", ch(op())); //ch 함수의 입력을 op의 출력값으로 놓을 수 있다.
}
char op() {
 puts("'c' 섭씨온도에서 화씨온도 변환");
 puts("'f' 화씨온도에서 섭씨온도 변환");
 puts("'q' 종료");
 char o;
 scanf(" %c", &o);
 return o;
}
double ch(char o) {
 double temp;
 scanf("%lf", &temp);
 switch (o)
 {
 case 'c':
 return 9.0 / 5.0\*temp + 32;
 case 'f':
 return (temp - 32.0)\*5.0 / 9.0;
 default:
 break;
 }
}
```





 


위 코드에서는 새로운 것이 2가지 나온다.

​

1. 함수원형

코드의 위에서는 선언만 하고 아래에 함수 내용을 써놓 수 있다,

2.함수의 입력을 함수의 출력으로 놓을 수 있다.

​




 




```
#include
int com(int n, int r);
int fact(int n);
int get(void);
int main(void) {
 int n, r;
 n = get();
 r = get();
 printf("C(%d, %d) =%d \n", n, r, com(n, r));
 return 0;
}
int com(int n, int r) {
 return (fact(n) / (fact(r)\*fact(n - r))); //함수의 반환을 입력으로 쓸 수 있다.
}
int fact(int n) {
 int i;
 int result = 1;
 for (i = 1; i <= n; i++)
 result \*= i;
 return result;
}
int get(void) {
 int n;
 puts("정수를 입력하세요 : ");
 scanf("%d", &n);
 return n;
}
```





 


위 코드는 조합(combination)을 구하는 코드입니다.

com,fact,get 함수가 있는데

get함수는 scanf로 받은 값을 반환시키는 역할을 합니다.

fact 함수는 입력된 수의 팩토리얼을 구한 후 반환합니다

com 함수는 




 






 


을 계산하는 함수입니다.

​

위 코드의 중요한 사실은 함수의 반환값을 새로운 함수의 입력값으로 쓸 수 있는 것입니다.

​

​




 




```
#include
int is\_prime(int n);
int get(void);
void result(int a);

int main(void) {
 result(is\_prime(get())); //get실행 후 반환값을 is\_prime에 넣고 그 반환값이 result로 들어간다
}

int is\_prime(int n) {
 for (int i = 2; i < n; i++)
 if (n%i == 0) {
 printf("약수 %d\n", i);
 return 0;

 }
 return 1;
}
int get(void) {
 int a;
 scanf("%d", &a);
 return a;
}
void result(int a) {
 a ? puts("소수입니다") : puts("소수가 아닙니다");
}
```





 


위 코드는 입력받은 정수가 소수인지 판별하는 프로그램이다

위 함수는 get,is\_prime,result가 있다.

get은 void를 인수로 가지고 int형을 반환한다.

반환하는 값은 scanf한 a이다.

​

is\_prime은 int를 인수로 가지고 int헝을 반환한다.

i가 1씩 올라가며 

만약(if) 인수 n을 i로 나눴을때 나머지가 0이라면, 즉 약수가 있다면 그n을 출력한다

그리고 0을 반환한다.

나눴을때 나머지가 0이되는 값이 없으면(약수가 없으면) 0을 반환한다.

is\_prime에서 반환받은 값은 result의 인수가 되는데 인수에 따라 소수인지 아닌지를 판별한다.

​

함수같은 경우에는 다시 말하지만 어떤 형태를 인수,반환 형태로 갖느냐가 매우 중요한 것 같다.

또 어느 기능적으로 함수를 나눌지에 따라 좋은 코드가 될 수 있고 나쁜 코드가 될 수 있다.

개발자의 센스가 매우 중요한 것 같은 기능이다. 

​

​




 

