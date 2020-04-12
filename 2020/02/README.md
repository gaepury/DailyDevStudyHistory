
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
* [Diving Deep Into Kubernetes Networking: Docker와 k8s 네트워크 분석](https://woohhan.github.io/study/k8s_networking_deep_diving/)
    * 한번 더 읽을필요가있다
* [가난한 스타트업의 WebRTC 백엔드 비용절감위한 고군분투기](https://blog.remotemonster.com/%EB%9D%BC%EC%9D%B4%ED%8A%B8%EC%84%B8%EC%9D%BC%EC%97%90-%EA%BE%B8%EC%97%AD%EA%BE%B8%EC%97%AD-%EC%98%A4%ED%86%A0-%EC%8A%A4%EC%BC%80%EC%9D%BC%EB%A7%81-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0-c31f467415d6)
    * aws 라이트세일
* [링크드인에서 사용중인 커스텀 Kafka 공개](https://blog.voidmainvoid.net/273)
* [개발자 머피의 법칙](https://woowabros.github.io/experience/2019/09/19/programmer-murphy-law.html)
    * 약간 웃기지만 중요한 메시지
    * 사용자는 실수한다, 사용자의 입력은 무조건 검증한다
        * 첫째 UI에서 선검증해서 편리성을 높이고(이건 말 그대로 편리성을 위한 것입니다), 그리고 서버측에서도 올바른 범위의 값을 입력했는지 무조건 검증해야만 합니다. 서버측 검증이 안 된 것은 클라이언트에서 어떤 3중 4중 검사해도 
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

--- 
## 2020.02.19(1개)
* [도커 네트워크 요약 (Docker Networking)](https://jonnung.dev/docker/2020/02/16/docker_network/)
    * none
        * 네트워크를 사용하지 않습니다. 따라서 컨테이너는 외부에서 접근할 수 없는 상태가 됩니다. --net=none 인자를 통해 None 네트워크 컨테이너를 생성할 수 있습니다.
    * host
        * 호스트의 네트워크 네임 스페이스를 그대로 공유합니다. 따라서 컨테이너와 호스트 사이의 네트워크에 대한 Isolation이 제공되지 않습니다
    * bridge
        * 리눅스 브릿지는 소프트웨어로 구현된 스위치
        * docker bridge
           * ![image](https://user-images.githubusercontent.com/20143765/74805184-be4f8800-5325-11ea-9fd9-b338973d4708.png)
        * Docker는 설치시 자동으로 docker0 브릿지를 생성하고 브릿지 네트워크로 실행된 컨테이너를 이 브릿지에 연결
        * 컨테이너는 Linux Namespace 기술을 이용해 각자 격리된 네트워크 공간을 할당받게 된다. 그리고 위에서 언급한 대로 172.17.0.0/16 대역의 IP를 순차적으로 할당 받는다. 이 IP는 컨테이너가 재시작할 때마다 변경될 수 있다. 컨테이너는 외부와 통신하기 위해 2개의 네트워크 인터페이스를 함께 생성한다. 하나는 컨테이너 내부 Namespace에 할당되는eth0 이름의 인터페이스이고, 나머지 하나는 호스트 네트워크 브릿지 docker0에 바인딩 되는 vethXXXXXXX이름 형식의 veth 인터페이스다. (“veth”는 “virtual eth”라는 의미)
컨테이너의 eth0인터페이스와 호스트의 veth 인터페이스는 서로 연결되어 있다. 결국 docker0 브리지는 각 veth인터페이스와 연결돼 호스트의 eth0 인터페이스와 이어주는 역할을 한다. 그리고 컨테이너의 eth0인터페이브스는 호스트의 veth인터페이스를 통해 외부와 통신할 수 있게 되는 것이다.
    * 참고
        * https://jonnung.dev/docker/2020/02/16/docker_network/
        * https://woohhan.github.io/study/k8s_networking_deep_diving/

---
## 2020.02.29(20개)
* [Spring Batch의 멱등성 유지하기](https://jojoldu.tistory.com/451)
    * LocalDate.now()같은게 코드내의 담겨있으면 재현하기 힘듬. 날짜를 JobParameter로 넘기자
* [HTTP/3: 과거, 현재 그리고 미래](https://blog.cloudflare.com/ko/http3-the-past-present-and-future-ko/)
    * HTTP/1.1
        * 단점
            * TCP + TLS 핸드쉐이크
                * ![image](https://user-images.githubusercontent.com/20143765/75607773-db623300-5b3d-11ea-9333-1e76aa80758e.png)
            * 슬로우 스타트
        * 킵 얼라이브로로도 하나씩 순서대로 보내야 하므로 각 연결에서는 한번에 하나의 요청/응답 교환만을 처리하므로 비효율적
    * HTTP/2
        * 스트림
            * 동일한 TCP 연결에 복수의 HTTP 응답/요청 교환을 동시 다중 송신할 수 있도록 하는 추상 개념
                *  모든 응답과 요청은 패킷 손실에 대해서 하나의 요청에만 관계된 것이라도 동등하게 같은 영향을 받습니다(네트워크 혼잡 상황). 이것은 HTTP/2 계층이 서로 다른 HTTP 응답/요청 교환을 별개의 스트림으로 분리 하였지만 TCP는 그러한 추상화에 대해 알지 못하므로 특별한 의미가 없는 바이트 열로만 보기 때문입니다.
    * HTTP/3
        *  QUIC 스트림은 동일 QUIC 연결을 공유 하므로 새 스트림을 만들 때 추가적인 핸드쉐이크나 슬로우 스타트가 필요하지 않습니다.
        * QUIC 연결
            * ![image](https://user-images.githubusercontent.com/20143765/75607782-e2894100-5b3d-11ea-9e38-bb35db7a639e.png)
            * HTTP의 첫 요청에 필요한 QUIC 연결을 새로 만들 때에도 데이터 전송 시작까지 걸리는 지연 시간은 TCP 상의 TLS보다 작습니다.
        * HTTP/2와 다른 헤더 압축기법
            * HPACK이라고 하는 HTTP/2의 헤더 압축 기법
* [LINE 인프라 플랫폼의 뒷이야기 – 서비스 확장성을 확보하며 운영 비용 줄이기](https://engineering.linecorp.com/ko/blog/challenges-and-solutions-of-line-infra-scaleout/)
* [Spring Batch 간단 정리](https://cheese10yun.github.io/spring-batch-basic/#undefined)
    * 청크 지향프러그래밍의 이점은 1000개 개의 데이터에 대해 배치 로직을 실행한다고 가정했을 때 청크로 나누지 않았을 때는 하나만 실패해도 다른 성공한 999개의 데이터가 롤백
    * 재시도 템플릿
        * RetryTemplate
* [캐시의 개념과 장점](https://feel5ny.github.io/2019/09/30/HTTP_007-1/#topology)
* [캐시의 원리와 제어방법](https://feel5ny.github.io/2019/10/05/HTTP_007-2/)
    * 캐시 재검사 시 가장 유용한 2가지 조건부 요청 헤더
        * If-Modified-Since: 날짜 재검사
           * reqeust 헤더
           * 서버에게 리소스가 특정 날짜 이후로 변경된 경우에만 요청한 본문을 보내달라고 한다.
           * 만약 문서가 주어진 날짜 이후에 변경되지 않았다면, 조건은(If-Modified-Since) 거짓이고 서버는 304 Not Modified 응답메세지를 클라에게 돌려준다.
           * If-Modified-Since 헤더는 Last-Modified 헤더와 함께 동작
        * If-None-Match: 엔터티 태그(ETag) 재검사
           * request 헤더
           * 캐시 된 태그가 서버에 있는 문서의 태그와 다를 때만 요청을 처리한다.
           * If-None-Match 헤더는 ETag 헤더와 함께 동작
    * 언제 엔터티 태그를 사용하고 언제 Last-Modified 일시를 사용하는가
        * HTTP/1.1 클라는 만약 서버가 엔터티 태그를 반환했다면, 반드시 엔터티 태그 검사기를 사용해야 한다.
        * Last-Modified 값만을 반환했다면 클라는 If-Modified-Since 검사를 사용할 수 있다.
        * 만약 HTTP/1.1 캐시나 서버가 If-Modified-Since와 엔터티 태그, 조건부 헤더를 모두 받았다면, 요청의 모든 조건부 헤더 필드의 조건에 부합해야 200을 반환해야 한다.
* [Google Code review Guide](https://wiki.lucashan.space/code-review/01.intro.html#_1-code%EB%A5%BC-%EB%A6%AC%EB%B7%B0%ED%95%98%EB%8A%94-%EC%82%AC%EB%9E%8C%EB%93%A4%EC%9D%80-%EC%96%B4%EB%96%A4%EA%B2%83%EC%9D%84-%EC%A4%91%EC%A0%90%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%82%B4%ED%8E%B4%EC%95%BC%ED%95%98%EB%8A%94%EA%B0%80)
    * Code를 리뷰하는 사람들은 어떤것을 중점적으로 살펴야하는가
        * 디자인(Design): 코드가 잘 설계되어 있고 시스템에 적합한가?
        * 기능성(Functionality): 코드가 작성자의 의도대로 동작하는가?
        * 복잡성(Complexity): 코드가 더 간단히 작성될 수 있는가? 다른 개발자가 코드를 쉽게 이해하고 사용 할 수 있는가?
        * 테스트(Tests): 코드에 정확하고 잘 설계된 자동 테스트가 있는가?
        * 이름짓기(Naming): 개발자가 변수, 클래스, 메소드(함수)등에 명확한 이름을 선택했는가?
        * 주석(Comments): 주석이 명확하고 유용한가?
        * 스타일(Style): 코드가 스타일 가이드를 따르는가?
            * 위의 링크는 google 스타일 가이드로 연결되지만, 각 조직의 스타일 가이드를 뜻한다고 봐도 무방합니다.
        * 문서화(Documentation): 개발자가 관련문서를 작성하거나 적절하게 업데이트 하였는가?
* [문제를 해결할 때 사고가 중요한 이유](https://engineering.linecorp.com/ko/blog/think-differently-to-solve-problems/)
* [서버 사이드 테스트 자동화 여정 – 1. 테스트 자동화를 시작한 계기와 그 첫 발걸음](https://engineering.linecorp.com/ko/blog/server-side-test-automation-journey-1/)
    * Pr hookd으로 별걸 다하네..
        * Unit test task
        * Configuration verification task
        * Infrastructure(연계모듈) check task
        * Performance task
* [서버 사이드 테스트 자동화 여정 – 2. 통합 테스트 수준의 회귀 테스트 환경 구축 및 Docker 활용](https://engineering.linecorp.com/ko/blog/server-side-test-automation-journey-2/)
    * 통합테스트
        * pytest
    * 통합테스트 보고서
        * pytest-html
    * 통합 테스트 보고서 생성 시간 단축하기
    * Docker를 이용하여 통합 테스트 환경 개선
    * 외부 시스템 의존 로직도 테스트할 수 있게 만들기 - 모의 서버 개발
        * ![image](https://user-images.githubusercontent.com/20143765/75607776-ddc48d00-5b3d-11ea-9571-083166af05db.png)
* [서버 사이드 테스트 자동화 여정 – 3. Docker를 활용한 통합 테스트 환경 개선](https://engineering.linecorp.com/ko/blog/server-side-test-automation-journey-3/);
    * 로깅
        * 디버깅 내용도 저장(Kibana 6.7의 Logs라는 기능을 이용하여 디버깅 내용도 보기에 적합)
    * 테스트 병렬화로 테스트 수행 시간 단축
    * 통합 테스트 실행 환경 준비 시간 단축하기
        *  Jenkins 라벨을 사용하면 잡이 실행될 노드를 지정
    * 최종 아키텍처
        * ![image](https://user-images.githubusercontent.com/20143765/75607785-e7e68b80-5b3d-11ea-8f7f-0546d4f93664.png)
* [[MSA] Spring Cloud Ribbon - 개념과 실습편](https://sabarada.tistory.com/54?category=822738)
    * Ribbon의 구성요소로는 Rule, Ping, ServerList
    * ServerList - 로드 밸런싱 대상 서버 목록
        * configuration을 통해 static 하게 설정 가능
        * eureka 등을 기반으로 dynamic하게 설정 가능
    * Rule - 요청을 보낼 서버를 선택하는 논리
        * Round Robbin - 한 서버씩 돌아가며 전달
        * Available Filtering - 에러가 많은 서버 제외
        * weighted Response Time - 서버별 응답 시간에 따라 확률 조절
    * Ping - 서버list가 살아있는지 체크하는논리
        * static, dynamic 모두 가능
    * Retry
    * RestTemplate에 적용 가능
* [[MSA] Spring Cloud Zuul 1.x - 개념편](https://sabarada.tistory.com/55?category=822738)
    * 기본 Type 필터에는 PRE, ROUTING, POST, ERROR
    * Filter들은 Chaining
    * Filter 키워드
        * Type : filter가 적용되는 시점(PRE, ROUTING, POST, ERROR).
        * Execution Order : fileter가 적용되는 시점(Type) 안에서의 순서
        * Criteria : Filter가 실행되는 조건
        * Action : Filter가 실행될 때 수행되는 실질적인 로직
* [[MSA] Spring Cloud Zuul 1.x - 실습편](https://sabarada.tistory.com/56?category=822738)
* [기술 뉴스 #144 : 20-02-15](https://blog.outsider.ne.kr/1477?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+rss_outsider_dev+%28Outsider%27s+Dev+Story%29);
     * Fe news
     * Grafana의 어노테이션 API를 이용해서 슬랙에 메시지를 남기면 해당 시점에 어노테이션을 Grafana 대시보드 상에 표시할 수 있는 슬랙봇 memo를 만들어서 공개했다.
* [Jackson 라이브러리 기본기능 정리 - json 직렬화와 역직렬화](https://pjh3749.tistory.com/281)
     * @JsonAnyGetter
         * 맵 필드를 풀어줌
     * @JsonValue
         * enum에서 getName 메서드에 @JsonValue를 넣어주어 이름을 통해 직렬화
     * 커스텀 직렬화, 역직렬화
         * @JsonSerialize, @JsonDeserialize
     * 역직렬화
         * @JsonCreator
     * @JacksonInject
         * @JacksonInject 는 json 데이터가 아닌 곳에서 값을 주입할 때 사용
     * @JsonAnySetter
         * 역직렬화 과정에 map에 담을때 유용
     * @JsonAlias
         * @JsonAlias는 역직렬화를 할 때 한 개 이상의 이름을 한 객체 필드에 매핑되게 설정
     * @JsonAutoDetect
         * @JsonAutoDetect를 이용하여 필드의 직렬화 대상을 지정
         * ```@JsonAutoDetect(fieldVisibility = JsonAutoDetect.Visibility.ANY)```
* [타다 웹 프론트엔드의 모든 것](http://engineering.vcnc.co.kr/2020/01/introduce-tada-web-frontend/)
* [Jackson custom serializer, deserializer 적용했던 사례 공유, LocalDateTime JSON 파싱하는 방법](https://jeong-pro.tistory.com/202);
    * custom serializer(StdSerializer 상속)
        * ```java 
            package com.tistory.jeongpro.util; 
            import java.io.IOException; 
            import java.time.LocalDateTime; 
            import java.time.format.DateTimeFormatter; 
            import com.fasterxml.jackson.core.JsonGenerator; 
            import com.fasterxml.jackson.databind.SerializerProvider; 
            import com.fasterxml.jackson.databind.ser.std.StdSerializer; 

            public class LocalDateTimeSerializer extends StdSerializer { 
               protected LocalDateTimeSerializer(Class<LocalDateTime> t) { super(t); } 
               public LocalDateTimeSerializer() { this(null); } /** * */ 
               private static final long serialVersionUID = -1636482041003741854L; 
               @Override public void serialize(LocalDateTime value, JsonGenerator gen, SerializerProvider provider) throws IOException {
                  gen.writeString(value.format(DateTimeFormatter.ofPattern("yyyy-MM-dd'T'HH:mm:ss.SSS"))); 
               } 
            }
         ```
    * custom deserializer(StdDeserializer 상속)
        * ``` java
            package com.tistory.jeongpro.util; 
            import java.io.IOException; 
            import java.time.LocalDateTime;
            import java.time.format.DateTimeFormatter; 
            import com.fasterxml.jackson.core.JsonParser;
            import com.fasterxml.jackson.core.JsonProcessingException; 
            import com.fasterxml.jackson.databind.DeserializationContext; 
            import com.fasterxml.jackson.databind.JsonNode;
            import com.fasterxml.jackson.databind.deser.std.StdDeserializer;
            import com.tistory.jeongpro.domain.User; 
   
            public class UserDeserializer extends StdDeserializer { 
               public UserDeserializer() { this(null); } 
               protected UserDeserializer(Class<?> vc) { super(vc); } 
               private static final long serialVersionUID = -7683857719562990174L;

               @Override 
               public User deserialize(JsonParser p, DeserializationContext ctxt) throws IOException, JsonProcessingException {   
                  JsonNode jsonNode = p.getCodec().readTree(p); 
                  long id = jsonNode.get("id").asLong(); 
                  String createdString = jsonNode.get("created").asText(); 
                  LocalDateTime created = LocalDateTime.parse(createdString, DateTimeFormatter.ISO_LOCAL_DATE_TIME);
                  LocalDateTime modifiedCreated = LocalDateTime.of(created.getYear(), created.getMonth(), created.getDayOfMonth(), created.getHour(), created.getMinute()); 
                  return new User(id, modifiedCreated); 
               } 
            }
         ```
    * Custom serializer, deserializer 모듈
        * ```java
            SimpleModule simpleModule = new SimpleModule(); 
            simpleModule.addSerializer(LocalDateTime.class, new LocalDateTimeSerializer());          
            simpleModule.addDeserializer(User.class, new UserDeserializer()); 
            objectMapper.registerModule(simpleModule);
          ```
* [[MSA] Spring Cloud Sleuth와 Zipkin을 이용한 분산 시스템 Tracing_1](https://sabarada.tistory.com/43)
    * [demo-order,5de772c409f727e933fc0d958149413e,33fc0d958149413e,false
    * demo-order[project 이름]
    * 5de772c409f727e933fc0d958149413e[TraceId]
        * transaction을 추적하기 위한 마이크로서비스간의 공통된 UUID
    * 33fc0d958149413e[SpanId]
        * 마이크로서비스에서 부여되는 UUID
    * false[exportable]
        * exportable은 zipkin이나 다른 곳으로 결과값을 전송하는지 유무
* [[MSA] Spring Cloud Sleuth와 Zipkin을 이용한 분산 시스템 Tracing_2](https://sabarada.tistory.com/44)
