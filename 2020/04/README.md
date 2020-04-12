## 2020.04.12
* [Outsider`s 기술 뉴스 #146 : 20-04-01](https://blog.outsider.ne.kr/1480?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+rss_outsider_dev+%28Outsider%27s+Dev+Story%29)
* [React Production Performance Monitoring](https://kentcdodds.com/blog/react-production-performance-monitoring)
    * React의 Profiler API를 이용해서 프로덕션 사이트에서 React의 성능을 측정해서 매트릭을 Grafana 등 백엔드로 전송하는 방법을 소개
* [Spring MVC - Understanding HandlerAdapter](https://www.logicbig.com/tutorials/spring-framework/spring-web-mvc/handler-adapter.html)
    * HandlerAdapters
        * RequestMappingHandlerAdapter(default)
        * HttpRequestHandlerAdapter(default)
        * SimpleControllerHandlerAdapter(default)
        * SimpleServletHandlerAdapter
    * RequestMappingHandlerAdapter
        * @RequestMapping이라는 애노테이션을 컨트롤러 클래스나 메서드에 선언하여 사용
        * 현재 대부분 이 방식으로 개발한다.
    * HttpRequestHandler, HttpRequestHandlerAdapter
        * 이 컨트롤러와 어댑터를 이용하면 자바의 RMI(Remote Method Invocation 원격지 메소드 호출) 기술을 HTTP기반으로 사용할 수 있다.
        * 이 컨트롤러는 모델과 뷰의 개념이 없는 서비스를 개발할 때 사용한다.
    * Controller, SimpleControllerHandlerAdapter
        * 이 컨트롤러는 스프링 MVC기술을 확장해서 전용 컨트롤러를 만들어 사용하려고 할 때 유용하다.
        * 컨트롤러가 특정 클래스를 상속하는데 문제가 없다면, Controller타입 인터페이스를 구현하는 공통 컨트롤러 클래스를 만들고 구현된 공통 컨트롤러를 상속받아서 개별적인 컨트롤러를 만들어 사용한다. 
    * Servlet, SimpleServletHandlerAdapter
        * 이 컨트롤러와 컨트롤러 어댑터는 기존 표준 서블릿(HttpSErvlet을 상속받아 정의하는 서블릿) 클래스 코드를 그대로 유지하면서 사용할 수 있도록한다.
* Reactive-Streams
   * https://jongmin92.github.io/2019/11/05/Java/reactive-1/
   * https://jongmin92.github.io/2019/11/07/Java/reactive-2/
   * https://jongmin92.github.io/2019/11/10/Java/reactive-3/
* [Spring Webflux + Reactor](https://dreamchaser3.tistory.com/6)
    * 1. Schedulers.immediate(): 현재 스레드
    * 2. Schedulers.single(): 단일의 재사용 가능한 스레드, 모든 호출자가 같은 스레드를 사용한다. 호출 때마다 새로운 스레드를 원한다면 Schedulers.newSingle()을 사용해야 한다.
    * 3. Schedulers.elastic(): elastic한 스레드 풀, 필요한 만큼 새 스레드 풀을 생성하고, 놀고 있는 스레드를 재사용한다. 너무 오래(기본 값 60초) 놀고 있는 스레드 풀은 폐기된다. I/O 블록킹 작업을 할 때 좋은 선택이다.
    * 4. Schedulers.parallel(): 병렬 작업을 하도록 튜닝이 된 고정 스레드 풀이다. CPU 코어 수 만큼의 워커 스레드를 생성한다. CPU-bound 블록킹 작업을 하기에 좋은 선택이다.
* [Reactor - Reactive Streams 생명주기](https://dreamchaser3.tistory.com/16)
    * 조립단계, 구독단계, 런타임단계
    * 조립단계
        * Flux,Mono를 만들어 연결
    * 구독단계
        * publisher에 subscribe()를 호출하였을 때 발생하는 단계
        * publisher 체인을 따라 subscribe()가 전파가 되기 때문에, 다음 체인의 Subscriber 생성자에 자기 자신을 파라미터로 전달하고, 그에 따라 publisher 체인과는 다시 반대 순서의 체인이 형성
    * 런타임단계
        * publisher와 subscriber가 onSubscribe() 시그널과 request() 시그널을 교환하면서 스트림 실행이 시작
        * Subscription::request() 메소드는 호출 시 요청 수요 정보를 volatile 필드에 쓴다. 이는 비용이 많이 드는 연산이므로 request() 호출이 적을수록 좋다.
* [Spring Webflux - DispatcherHandler](https://dreamchaser3.tistory.com/12)
    * Request 처리 과정
        * ![image](https://user-images.githubusercontent.com/20143765/79060177-d3f58400-7cbc-11ea-8de8-2a89f76f21f5.png)
    * Special Bean Types
        * ![image](https://user-images.githubusercontent.com/20143765/79060178-d821a180-7cbc-11ea-8208-0efdde42366f.png)
    * Processing
        * 각 HandlerMapping이 핸들러를 매칭하도록 요청 받고, 첫 번째로 매칭이 된 것이 사용된다.
        * 적절한 HandlerAdapter를 통해 핸들러가 실행이 되고, return value는 HandlerResult로 랩핑된다.
        * HandlerResult는 적절한 HandlerResultHandler에 넘어가고, response를 바로 쓰거나 view를 렌더링하면서 처리가 완료된다.
    * Result Handling
        * ![image](https://user-images.githubusercontent.com/20143765/79060179-dce65580-7cbc-11ea-9bf9-e57ff2e9206b.png)
    * Exceptions
        * HandlerAdapter로부터 리턴된 HandlerResult는 다음과 같은 경우에 error function을 호출한다.
            * 핸들러 처리가 실패한 경우
            * HandlerReusltHandler가 핸들러 리턴 값 처리를 실패한 경우
        * webflux에서는 핸들러가 맵핑이 된 이후에 발생한 에러만 처리가 가능(mvc에서는 전후 가능)
    * View Resolution
        * 핸들러의 return 값은 그 타입에 따라 다음 중 하나로 처리된다.
            * String, CharSequence: view name으로 간주하고 ViewResovler를 통해 해당 이름의 파일을 찾아서 View객체로 만든다.
            * void: request path에 따른 default view 이름을 골라서 View객체로 만든다. 이 경우는 void 타입의 리턴 뿐만 아니라 view 이름이 지정되지 않았을 때(ex. model attribute 리턴, Mono<Void>)에도 해당된다.
            * Rendering: view resolution과 관련된 API를 제공한다. 관련 문서 참고
            * Model, Map: 요청의 model에 이 attributes를 추가로 더한다.
            * 기타: 기타 리턴 값은 model attribtue에 추가로 더한다.
* [Spring WebFlux - Config](https://dreamchaser3.tistory.com/15)
    * WebFluxConfigurer interface 구현
    * Conversion, formatting
        * addFormatters method overide(자세한것은 링크 참고)
    * Content Type Resolvers
        * query parameter-based 방식을 사용가능(디폴트는 accept header)
        * configureContentTypeResolver method override(자세한것은 링크 참고)
    * HTTP message codecs
        * configureHttpMessageCodecs method override (자세한것은 링크 참고)
    * View Resolvers
        * configureViewResolvers method override(자세한것은 링크 참고)
    * Static Resources
        * addResourceHandlers method overide(자세한것은 링크 참고)
    * Path Matching
        * configurePathMatch method overide(자세한것은 링크 참고)
    * Advanced Configuration mode
        * DelegatingWebFluxConfiguration을 import(자세한것은 링크 참고)
