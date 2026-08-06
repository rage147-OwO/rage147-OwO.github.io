---
title: "ARM TrustZone (트러스트 존)"
date: 2025-12-16
categories:
 - Keomgong
naver_url: https://blog.naver.com/rage147-owo/224112144386
---

ARM CPU 아키텍쳐에는, TrustZone이라는 보안 기술이 있다.

바로 하나의 CPU를 두 개의 논리적인 실행 영역으로 나누는 기술이다.

Normal World와 Secure World로 나눠지는 이 영역은 크게 아래와 같다.

![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/224112144386/06457655321c.png)

애플리케이션 단에서 OS를 통해 Secure Monitor Call(SMC) 을 요청하면, Secure World로 전환되고 그 안에서 Trusted OS가 인증 관련 처리를 진행하는 그런 식이다.

이 때 Secure World로 진입하기 위해 Monitor를 Call하는 것을 Secure Monitor Call(SMC) 이라고 한다.

Trust OS는 사용자가 사용하는 OS(Windows, Ubuntu)와는 무관하게, ARM CPU 아키텍쳐 내부에서 독립적으로 실행된다.

그리고 사용자 OS가 아는 것은 인증 등록 방법과 인증 요청 방법, 즉 그러한 Call 방법(API) 뿐이다.

아 참. 이렇게 나누는 이유는, OS가 탈취당하거나 악성 OS일 때, 내부의 인증 키나 보안 정보를 보호하기 위함이다.

Secure World 내부에서는 하드웨어 고유 ID(HW Root Key) 를 사용하고, 이 ID는 Trust OS만 알기 때문에 사용자 OS와는 무관하게 보안 연산이 수행된다.

따라서 Secure World에 대한 접근은 SMC를 통해서가 아니면 불가능하다.

그리고 핵심은, SMC를 통해 요청하더라도 반환되는 것은 내부 정보가 아니라 연산 결과 데이터만 반환된다는 점이다.

즉, 인증 등록, 인증 진행, 인증 삭제와 같은 검증/연산 과정만 요청할 수 있을 뿐, 직접적인 메모리 덤프나 특정 내부 데이터를 읽는 기능은 SMC 자체에 정의되어 있지 않다.

또한 TrustZone 내부에서는 보안 자산을 보호하기 위한 정책도 함께 관리한다.

어떤 프로세스에서 SMC를 호출했는지, 얼마나 자주 호출했는지, 앱 삭제나 OS 초기화 시에 키의 영속성을 어떻게 처리할지와 같은 부분들도 Secure World 내부 정책으로 관리된다.

이게 TrustZone의 기본적인 동작 방식이다.

물론 이러한 기술이 만능은 아니다.

실제로 CVE-2015-6639와 같은 보안 취약 사례에서는 TrustZone 내부에서 동작하던 기술 중 QSEE(Qualcomm Secure Execution Environment) 와 그 안의 Keymaster 구현이 깨진 경우가 있었다.

이 취약점은 TrustZone이라는 구조 자체가 무너진 것이 아니라, Secure World 내부에서 실행되던 소프트웨어 로직의 취약점으로 인해 의도하지 않은 동작이 가능해진 사례였다.

즉, Normal World에서 권한을 획득한 공격자가 SMC를 통해 Secure World로 요청을 전달하고, 그 요청을 처리하던 Keymaster 로직의 취약점을 악용해 암호 키 보호 로직을 우회할 수 있었던 것이다.

이로 인해 전체 디스크 암호화(FDE)와 같이 TrustZone 기반으로 동작하던 보안 기능들까지 연쇄적으로 영향을 받게 되었다.

이 사례가 보여주는 점은 명확하다.

TrustZone은 하드웨어 수준에서 영역을 분리해주는 강력한 기반이지만, 그 위에서 동작하는 Secure World 내부 소프트웨어까지 자동으로 안전하게 만들어주지는 않는다.

결국 TrustZone은 침입을 완전히 막는 기술이라기보다는, 피해 범위를 제한하기 위한 보안 구조에 가깝다.

Secure World 내부의 구현이 취약하다면, 그 위에 의존하고 있던 보안 기능 역시 같이 무너질 수 있다.

그럼에도 불구하고, OS가 침해된 상황에서도 보안 키와 인증 로직을 보호하기 위한 현실적인 해법이라는 점에서 여전히 중요한 보안 기술이다.

<https://www.boannews.com/media/view.asp?idx=51117>

[![](https://dthumb-phinf.pstatic.net/?src=%22http%3A%2F%2Fwww.boannews.com%2Fmedia%2FupFiles%2Fdisk.jpg%22&type=ff120)](https://www.boannews.com/media/view.asp?idx=51117)
[**전체 디스크 암호화 무력화시키는 취약점 발견**

안드로이드 환경에서 권한을 상승시켜주는 취약점이 발견되었다. 특히 이 취약점은 구글이 안드로이드 5.0 롤리팝 버전부터 도입한 전체 디스크 암호화(Full Disk Encryption, 이하 FDE) 보안 기능도 우회할 수 있도록 하는 것이라 매우 치명적이라고 전문가들은 평가했다.

www.boannews.com](https://www.boannews.com/media/view.asp?idx=51117)