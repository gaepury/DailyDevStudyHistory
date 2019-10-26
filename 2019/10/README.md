10월부터 링크 연결 및 간단한 요약 정리 

## 2019.10.06
* Cache-Aside Pattern in Redis
* [번역] OOP를 빨리 잊을 수록 여러분과 여러분의 소프트웨어에 좋습니다
    - 단점
        - 간단한 문제가 OOP 방식으로 프로그램을 짰더니 엄청난 양의 코드가 되어버린 이유는 언제나 추상화할 구석이 남아있기 때문입니다.
        - 당신은 바나나를 원했지만 실제로는 바나나를 들고 있는 고릴라와 정글 전체를 얻고 말았다.
        - 간단한 데이터 변형을 하는데 이상하고, 배배 꼬인 메서드끼리 호출
        - 수많은 보일러플레이트를 만들게 되죠. 게터(getter), 세터(setter), 다중 생성자, 이상한 메서드들 모두 실제로는 거의 일어나지 않을 실수로부터 보호하기 위한 방책입니다
* 3년차 웹 개발자
* 자바 메모리 관리 - 스택 & 힙
    * 메서드 호출시 파라미터가 스택에 쌓인다.
* 기능 요구사항 명세(Specification)
* 154. [Security] SSL과 인증서 구조 이해하기 : CA (Certificate Authority) 를 중심으로 
    * 인증서 내용물
       * ![image](https://user-images.githubusercontent.com/20143765/66271998-2766bf80-e89f-11e9-95c0-29dfaca7103e.png)
* [기술블로그 구독서비스 개발 후기 - 3부](https://taetaetae.github.io/2019/02/17/daily-dev-blog-3/)
* [Spring Guide - Domain](https://cheese10yun.github.io/spring-guide-domain/)
    * 객체지향에서 중요한 것들이 많겠지만 그중에 하나가 객체 본인의 책임을 다하는 것입니다. 여러번 반복해서 언급하지만, 객체가 자기 자신의 책임을 다하지 않으면 그 책임은 다른 객체에게 넘어가게 됩니다.
* [Effective Java3/E - 람다와 스트림](https://brunch.co.kr/@oemilk/207)
* [스프링 애플리케이션이 시작, 종료될 때 수행할 메서드 지정하는 방법 + 스프링 빈(Bean)이 생성, 소멸될 때 수행할 메서드 지정하는 방법(graceful 종료, CommandLineRunner, ApplicationListener, InitializingBea..](https://jeong-pro.tistory.com/179)
   - 요약
      - PostConstruct, CommandLineRunner(run method), ApplicationListener(onApplicationEvent method), InitializingBean(afterPropertiesSet method), DisposableBean(destory method)
      - PostConstruct 메서드 다음에 afterPropertiesSet 호출
``` java
@Service
public class TestService implements CommandLineRunner, ApplicationListener<ContextClosedEvent>, InitializingBean, DisposableBean {
    @PostConstruct
    private void init() {
        System.err.println("PostConstruct annotation으로 빈이 완전히 생성된 후에 한 번 수행될 메서드에 붙입니다.");
    }
    @Override
    public void run(String... args) throws Exception {
        System.err.println("commandLineRunner 인터페이스 구현 메서드입니다. '애플리케이션'이 실행될 때 '한 번' 실행됩니다.");
    }
    @Override
    public void onApplicationEvent(ContextClosedEvent event) {
        System.err.println("ApplicationListener<ContextClosedEvent> 인터페이스 구현 메서드 입니다. '애플리케이션'이 죽었을 때 '한 번' 실행됩니다.");
        System.err.println("이벤트 발생 시간(timestamp) : " + event.getTimestamp());
    }
    @Override
    public void afterPropertiesSet() throws Exception {
        System.err.println("InitializingBean 인터페이스 구현 메서드입니다. TestService 'Bean'이 생성될 때 마다 호출되는 메서드 입니다.");
    }
    @Override
    public void destroy() throws Exception {
        System.err.println("DisposableBean 인터페이스 구현 메서드입니다. TestService 'Bean'이 소멸될 때 마다 호출되는 메서드입니다");
    }
}
```
* [테스트 코드 없이 레거시 코드를 다 감수하시겠습니까?](http://woowabros.github.io/experience/2019/02/27/Working_Effectively_with_Legacy_Code.html)
* [aop를 이용한 oauth2 캐시 적용하기](http://woowabros.github.io/experience/2019/03/05/aop-oauth2-redis.html)
* [테크니컬 라이팅 컨퍼런스: API the Docs Chicago 2019 방문기](https://engineering.linecorp.com/ko/blog/api-the-docs-chicago-2019-recap/)
    * Docsops
    * 포드는 DocOps를 통해 분산되어 있는 API 접근 채널을 단일화
    * 리퀘스트 바디(body) 파라미터는 적어도 문단 하나 정도의 분량은 있어야 하며, 파라미터 예제 값과 엔드포인트를 호출하는 예제 코드도 함께 있는게 좋다.
* [로우 레벨로 살펴보는 Node.js 이벤트 루프](https://evan-moon.github.io/2019/08/01/nodejs-event-loop-workflow/index.html)
   * 요약
      * 이벤트 루프는 작업 스택을 가지고 있지 않다.
      * 이벤트 루프가 별도의 스레드에서 실행되고 자바스크립트 실행은 어떤 큐에서 하나씩 꺼내와서 다른 곳에서 하는 것이 아니라 자바스크립트의 실행 자체가 이벤트 루프 안에서 수행되는 것이다.
      * setImmediate는 콜백을 작업 큐의 앞 쪽에 밀어넣는 것이 아니라 setImmediate 만을 처리하기 위한 전용 페이즈와 큐가 존재한다.
      * setImmediate은 실질적으로 다음 페이즈 혹은 다음 이벤트 루프의 순회에서 실행되고, nextTick이 오히려 실질적으로 더 빠르게 실행된다.
      * nextTickQueue에 담긴 작업이 재귀 호출을 수행하는 경우 Node.js의 작업 프로세스를 블록킹할 수 있다. 주의하도록 하자.
* [[Shell Script] 산술식 수행하기 (더하기, 곱하기, 나누기, 빼기)](https://rim0621.tistory.com/90)
* [[Shell Script] 파일인지 폴더인지 if문 및 옵션](https://rim0621.tistory.com/91)
* [[Shell Script] case문 (요일별로 동작하기 좋네)](https://rim0621.tistory.com/92)
* [[Shell Script] for문 여러 형식](https://rim0621.tistory.com/93)
* [[Shell Script] while문, until문](https://rim0621.tistory.com/94)
* [Spring5 리액티브 스트림 정리 및 api 전달 방식 정리](https://wedul.site/624)
* [디자인 패턴 06 - 어댑터 (Adapter)](https://dhsim86.github.io/programming/2019/08/17/design_patterns_06-post.html)
* [디자인 패턴 07 - 가교 (Bridge)](https://dhsim86.github.io/programming/2019/08/17/design_patterns_07-post.html)
* [LINE Manga 데이터베이스 샤딩 – 데이터베이스 엔지니어 편](https://engineering.linecorp.com/ko/blog/line-manga-database/)
* [gRPC](https://ssup2.github.io/theory_analysis/gRPC/)
   * 아키텍처
      * ![image](https://user-images.githubusercontent.com/20143765/66271895-4749b380-e89e-11e9-9f86-a5c21266218b.png)
   * Protobuf 이용
      * ![image](https://user-images.githubusercontent.com/20143765/66271890-313bf300-e89e-11e9-8559-1d619d59fe60.png)
   * vs HTTP/1.1 + JSON
      * gRPC가 현재 주목받는 가장큰 이유는 기존의 HTTP/1.1 + JSON Protocol보다 빠르기 때문이다. HTTP/1.1과 JSON은 Text Protocol인 만큼 성능면에서는 불리하다. gRPC에서 이용하는 HTTP/2와 ProtoBuf는 Binray Protocol인만큼 상대적으로 적은양의 Packet을 주고 받는다. 또한 gRPC는 HTTP/2에서 지원하는 Connection Multiplexing, Server/Client Streaming을 이용하여 효율성을 좀더 끌어 올리고 있다.
* [빅데이터 처리 후기 (검색엔진 처리)](https://blog.lael.be/post/9242)
* [GeoJSON Format(형식)](http://www.gisdeveloper.co.kr/?p=8002)
```
{
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [102.0, 0.5]
            },
            "properties": {
                "prop0": "value0"
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "LineString",
                "coordinates": [[102.0, 0.0], [103.0, 1.0], [104.0, 0.0], [105.0, 1.0]]
            },
            "properties": {
                "prop0": "value0",
                "prop1": 0.0
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Polygon",
                "coordinates": [[[100.0, 0.0], [101.0, 0.0], [101.0, 1.0],[100.0, 1.0], [100.0, 0.0]]]
            },
            "properties": {
                "prop0": "value0",
                "prop1": { "this": "that" }
            }
        }
    ]
}
```

## 2019.10.12
 * [Jackson 관련](https://happyer16.tistory.com/entry/Jackson-%EA%B4%80%EB%A0%A8)
     * @JsonManagedReference : 해당 부분이 serialize 된다
     * @JsonBackReference : serialize 에서 제외 된다.
 * [효율적인 도커 이미지 만들기 #1 - 작은 도커 이미지](https://bcho.tistory.com/1356?category=731548)
 * [효율적인 도커 이미지 만들기 #2 - 도커 레이어 캐슁을 통한 빌드/배포 속도 높이기](https://bcho.tistory.com/1357)
     * jar 파일을 풀어서 라이브러리 jar파일들이 캐싱 대도록 레이어 분리


## 2019.10.15
 * [2019.10.10 - 토비의 스프링을 읽으며](https://blog.naver.com/writer0713/221674259511)
 * [Outsider 기술 뉴스 #136 : 19-10-15](https://blog.outsider.ne.kr/1463)
 * [Outsider 기술 뉴스 #136 : 19-09-02](https://blog.outsider.ne.kr/1458)
 * [Outsider 기술 뉴스 #136 : 19-09-15](https://blog.outsider.ne.kr/1460)
 * [Leon Sans : 동적으로 폰트의 웨이트를 바꿀 수 있고 애니메이션을 추가할 수 있는 폰트.](https://github.com/cmiscm/leonsans)
    * 인터렉티브 웹개발 토이프로젝트시 참고할만할듯
    
## 2019.10.22
* [키바나 Aggregation Size 옵션 특징](http://kangmyounghun.blogspot.com/2019/10/aggregation-size.html)

## 2019.10.26
* [Redis에서 Pub/Sub 방식 소개 및 Spring Boot에서 구현해보기](https://wedul.site/627)
* [[logstash] plugin-input-mongodb을 이용하여 mongoldb 기반 pipeline 구축](https://blog.naver.com/pjt3591oo/221624138418)
    * logstash-input-mongodb
    * logstash-output-mongodb 
        * 위 플러그인들을 이용하여 몽고와 logstash를 바로 연결 가능 
* [python scikit learn 데이터 전처리 방법 - 머신러닝 data preparecessing](https://lsjsj92.tistory.com/511)
    * Label encoding, one-hot encoding, feature scaling(StandardScaler, MinMaxScaler) 
