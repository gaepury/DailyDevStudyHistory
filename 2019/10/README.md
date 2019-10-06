### 2019.10.06
* Cache-Aside Pattern in Redis
* [번역] OOP를 빨리 잊을 수록 여러분과 여러분의 소프트웨어에 좋습니다
    * 단점
        *  간단한 문제가 OOP 방식으로 프로그램을 짰더니 엄청난 양의 코드가 되어버린 이유는 언제나 추상화할 구석이 남아있기 때문입니다.
        * 당신은 바나나를 원했지만 실제로는 바나나를 들고 있는 고릴라와 정글 전체를 얻고 말았다.
        * 간단한 데이터 변형을 하는데 이상하고, 배배 꼬인 메서드끼리 호출
        * 수많은 보일러플레이트를 만들게 되죠. 게터(getter), 세터(setter), 다중 생성자, 이상한 메서드들 모두 실제로는 거의 일어나지 않을 실수로부터 보호하기 위한 방책입니다
* 3년차 웹 개발자
* 자바 메모리 관리 - 스택 & 힙
    * 메서드 호출시 파라미터가 스택에 쌓인다.
* 기능 요구사항 명세(Specification)
* 154. [Security] SSL과 인증서 구조 이해하기 : CA (Certificate Authority) 를 중심으로 
    * 인증서 내용물
        * 몰라
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
    * 이벤트 루프는 작업 스택을 가지고 있지 않다.
    * 이벤트 루프가 별도의 스레드에서 실행되고 자바스크립트 실행은 어떤 큐에서 하나씩 꺼내와서 다른 곳에서 하는 것이 아니라 자바스크립트의 실행 자체가 이벤트 루프 안에서 수행되는 것이다.
    * setImmediate는 콜백을 작업 큐의 앞 쪽에 밀어넣는 것이 아니라 setImmediate 만을 처리하기 위한 전용 페이즈와 큐가 존재한다.
    * setImmediate은 실질적으로 다음 페이즈 혹은 다음 이벤트 루프의 순회에서 실행되고, nextTick이 오히려 실질적으로 더 빠르게 실행된다.
    * nextTickQueue에 담긴 작업이 재귀 호출을 수행하는 경우 Node.js의 작업 프로세스를 블록킹할 수 있다. 주의하도록 하자.
