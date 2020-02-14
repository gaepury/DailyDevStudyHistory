
## 2020.02.11(2개)
* [Spring RSocket Getting Started - 1 (Request / Response)](https://blog.naver.com/PostView.nhn?blogId=gngh0101&logNo=221788278405&parentCategoryNo=&categoryNo=38&viewDate=&isShowPopularPosts=false&from=postView)
* [Spring RSocket Getting Started - 2 (Fire And Forget)](https://blog.naver.com/PostView.nhn?blogId=gngh0101&logNo=221803996054&parentCategoryNo=&categoryNo=38&viewDate=&isShowPopularPosts=false&from=postView)

---

## 2020.02.13(7개)
* [함수형 사고와 Ramda.js로 기업 데이터 처리하기 (2)](https://www.huskyhoochu.com/functional-thinking-advanced/)
* [GitOps와 ArgoCD](https://coffeewhale.com/kubernetes/gitops/argocd/2020/02/10/gitops-argocd/)
    * 배포 관점에서 Single source of truth (SSOT)
        * 단일한 방법으로의 소프트웨어 배포
        * 항상 원천의 상태를 완벽히 반영하는 배포
    * GitOps에서는 배포상태의 모습을 항상 원천과 동일하게 맞출려고 노력
    * Gitops 원칙
        1. 선언형 배포 작업 정의서
        2. Git을 이용한 배포 버전 관리
        3. 변경 사항 운영 반영 자동화
        4. 자가 치유 및 이상 탐지
* [ving Deep Into Kubernetes Networking: Docker와 k8s 네트워크 분석](https://woohhan.github.io/study/k8s_networking_deep_diving/)
    * 한번 더 읽을필요가있다
* [가난한 스타트업의 WebRTC 백엔드 비용절감위한 고군분투기](https://blog.remotemonster.com/%EB%9D%BC%EC%9D%B4%ED%8A%B8%EC%84%B8%EC%9D%BC%EC%97%90-%EA%BE%B8%EC%97%AD%EA%BE%B8%EC%97%AD-%EC%98%A4%ED%86%A0-%EC%8A%A4%EC%BC%80%EC%9D%BC%EB%A7%81-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0-c31f467415d6)
    * aws 라이트세일
* [링크드인에서 사용중인 커스텀 Kafka 공개](https://blog.voidmainvoid.net/273)
* [개발자 머피의 법칙](https://woowabros.github.io/experience/2019/09/19/programmer-murphy-law.html)
    * 약간 웃기지만 중요한 메시지
    * 사용자는 실수한다, 사용자의 입력은 무조건 검증한다
    * 사용자는 다 안다, 사용자의 입력은 무조건 검증한다
        * 모든 계산은 서버에서 해야하고, 파라미터로 넘어온 값은 무조건 검증해야한다.
        * 사용자의 요청에 의해 Query의 모든 조건이 사라지면 안 된다
        * 조회 조건 유사 사례 - 믿는 개발자에게 뒤통수 맞는다
    * 성능 측정 없는 캐시 사용은 성능을 저해시킬 수 있으며 캐시 데이터 구조 변경을 조심스럽게 해야한다
    * 인증과 권한은 다르다 - 인증 후 권한 검사까지 필수
    * 사용자의 로그인 실패횟수를 트래킹하고, 일정 횟수 이상 실패시 로그인을 거부하거나 Captcha를 요구해야한다
    * 사용자의 가상 재화는 별도 결제 수단처럼 독립 인증해야한다
    * 직원의 PC에서 운영 서버 API, DB 저장소에 접근을 통제해야 한다
    * 중요 Batch 는 실행 여부를 제 3의 시스템에서 검증해야한다
    * Log를 외부 서버로 수집하는 것은 별도 프로세스에서 비동기로
    * Primary Key는 int 가 아니라 long 으로
    * 에러 로그는 일괄 알림을 하면 안되고, 일상적인 것과 Critical 한 것을 구분해
    * 롤백 가능한 배포
        * 웹 and 배치 모두
    * 당신의 서버는 무조건 죽는다 - SPoF를 제거하자
* [Spring AOP 동작 방식, 원리](https://hyungyu-lee.github.io/articles/2019-10/how-spring-aop-works)
    1. AopProxy 라는 Delegator 인터페이스로 표현되며 Dynamic Proxy 기반은 JdkDynamicAopProxy 클래스, Cglib 기반은 CglibAopProxy 클래스이다.
    2. Dynamic Proxy 기반과 Cglib 차이는 어떻게 프록시 객체를 생성하는지 방식 차이이다.
    3. Dynamic Proxy 는 프록시 객체 생성을 위해 인터페이스를 필수로 구현해야하며, Cglib 은 인터페이스를 구현하지 않은 일반 클래스에 런타임 시 코드 조작으로 프록시 객체를 생성해준다.
    4. DefaultAopProxyFactory 클래스의 createAopProxy 메소드를 통해 AopProxy 의 실 구현체가 생성된다.
       - 1. AOP 적용 대상이 인터페이스거나 인터페이스를 구현(implement)하고 있으면 JdkDynamicAopProxy 가 생성된다.
       - 2. 위 경우가 아니면 ObjenesisCglibAopProxy 기반 실 객체가 생성된다.
       - 3. Objenesis 는 과거 Cglib 의 몇 가지 단점을 해결해주는 라이브러리
    5. Transaction 대상의 경우 기본이 Cglib 으로 생성하게 설정되어있다.
       - 1. 성능상 Cglib 이 이점이 많고, 예외발생 확률도 적다고 한다.
       - 2. Cglib 이 가지고 있던 몇 가지 문제점들을 Objenesis 라이브러리를 통해 해결했다. (생성자 중복 호출, default 생성자 필요 문제 등)
    6. 기본 Spring AOP 이외에 스프링에서 사용할 수 있는 방법으로는 AspectJ 가 있다.
    7. Spring AOP 가 제공하는 프록시 기반 방식은 런타임 위빙 (RTW) 이라는 방식으로 프로그램 구동중에 위빙이 일어난다. 반면 AspectJ 는 컴파일 단계 또는 로드타임에 코드를 삽입하여(위빙) RTW 보다 성능면에서 우세하다. (CTW : 컴파일 타임 위빙, LTW : 로드 타임 위빙). 또한 AspectJ 는 기본 Spring AOP 보다 보다 다양한 포인트컷을 지원한다.
    8. 일반적인 경우 Spring AOP 에서 지원하는 방식으로 요구사항들이 충분히 해결되는 경우가 많고, 성능 또한 @AspectJ 갯수에 따라 달라지는데 일반적인 경우에서는 크게 체감하기 힘들다는 평이 있다.
    9. AspectJ 를 사용하기 위해서는 AJC 등 별도의 컴파일러 설정 등 추가 설정이 필요한데, Spring AOP 는 그렇지 않다.
