## 2020.04.12(24개)
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

* [사용하면서 알게 된 Reactor, 예제 코드로 살펴보기](https://tech.kakao.com/2018/05/29/reactor-programming/);
    * 바구니 속 과일 종류(중복 없이) 및 각 종류별 개수 나누기 예제
    * subscribeOn, publishOn
    * Schedulers.parallel() 사용
    * basket당 하나의 스트림만 공유하며 과일종류와 개수 뽑아내기
        * Hot, cold
        * Connectable Flux
            * connect(), publish(), autoConnect(), refCount()
    * 디버깅 활성화
        * Hooks.onOperatorDebug();
* [Project Reactor 4. Flux, Mono](https://brunch.co.kr/@springboot/154)
    * Mono Lifecycle
        * ![image](https://user-images.githubusercontent.com/20143765/79065317-61030200-7cea-11ea-8d18-d5abafa621ac.png)
* [Project Reactor 5. Subscriber](https://brunch.co.kr/@springboot/155)
    * subscribe 메서드들
        * ![image](https://user-images.githubusercontent.com/20143765/79065320-66604c80-7cea-11ea-98db-2be05dd963c2.png)
    * Back pressure
        * subscribe(consumer, errorConsumer, completeConsumer, subscriptionConsumber)
        * ![image](https://user-images.githubusercontent.com/20143765/79065323-6b250080-7cea-11ea-8635-6e073de6f6e0.png)
            * 결과는 에디킴만 보냄.
    * subscriber를 직접받아서 하는방법도 있지만 비추천
        * onSubscribe, onNext, onComplete, onError를 모두 직접 구현해야함
* [Project Reactor 6. Data Processing](https://brunch.co.kr/@springboot/156)
    * Filtering method: filter, take, skip, repeat 등
    * Converting method: map, flatmap, zip등
    
* [스프링 리액터 시작하기 1 - 리액티브 스트림 Flux Mono Subscriber](https://javacan.tistory.com/entry/Reactor-Start-1-RS-Flux-Mono-Subscriber)
    * 콜드 시퀀스 vs 핫 시퀀스
        * 시퀀스는 구독 시점부터 데이터를 새로 생성하는 콜드(cold) 시퀀스와 구독자 수에 상관없이 데이터를 생성하는 핫(hot) 시퀀스로 나뉜다.
* [스프링 리액터 시작하기 2 - 시퀀스 생성 just, generate](https://javacan.tistory.com/entry/Reactor-Start-2-RS-just-generate)
    * Flux.just(), Mono.just()로 만들기
    * Flux.range()로 정수 생성하기
    * Flux.generate() 메서드로 Flux 만들기
       * `Flux<T> generate(Callable<S> stateSupplier, BiFunction<S, SynchronousSink<T>, S> generator)`
       * `Flux<T> generate(Callable<S> stateSupplier, BiFunction<S, SynchronousSink<T>, S> generator, Consumer<? super S> stateConsumer)`
          * stateSupplier는 값을 생성할 때 사용할 최초 상태이다. BiFunction 타입의 generator는 인자로 상태와 SynchronousSink를 입력받아 결과로 다음 상태를 리턴하는 함수

* [스프링 리액터 시작하기 3 - 시퀀스 생성 create, stream](https://javacan.tistory.com/entry/Reactor-Start-3-RS-create-stream)
    * Flux.create()를 이용한 pull 방식 메시지 생성
        * Flux.generate()와의 차이점은 Flux.generate()의 경우 한 번에 한 개의 next 신호만 발생할 수 있었던 데 비해 Flux.create()는 한 번에 한 개 이상의 next() 신호를 발생할 수 있다는 점
    * Flux.create()를 이용한 push 방식 메시지 생성
    * Flux.fromStream(), Flux.fromIterable()을 이용한 Flux 생성
* [스프링 리액터 시작하기 4 - 시퀀스 변환 기초](https://javacan.tistory.com/entry/Reactor-Start-4-tbasic-ransformation)
    * Flux기반
    * map, flatmap, filter
    * 빈 시퀀스인 경우 기본 값 사용하기: defaultIfEmpty
    * 빈 시퀀스인 경우 다른 시퀀스 사용하기: switchIfEmpty
    * 특정 값으로 시작하는 시퀀스로 변환: startWith
    * 특정 값으로 끝나는 시퀀스로 변환: concatWithValues
    * 시퀀스 순서대로 연결: cancatWith
    * 시퀀스 발생 순서대로 섞기: mergeWith
        * 시퀀스의 연결 순서가 아니라 시퀀스가 발생하는 데이터 순서대로 섞고 싶다면 mergeWith()를 사용
    * 시퀀스 묶기: zipWith
    * 시퀀스 묶기: combineLatest
        * 발생한 개수를 맞춰서 쌍을 만드는 zipWith()와 달리 combineLatest()는 가장 최근의 데이터를 쌍으로 만든다. 다음은 그 차이를 보여준다.
    * 지정한 개수/시간에 해당하는 데이터만 유지: take, takeLast
    * 지정한 개수/시간만큼 데이터 거르기: skip, skipLast
* [스프링 리액터 시작하기 5 - 에러 처리](https://javacan.tistory.com/entry/Reactor-Start-5-error-handling)
    * subscribe의 errorConsumer 이용
    * 에러 발생하면 기본 값 사용하기: onErrorReturn
        * `Flux<T> onErrorReturn(Predicate<? super Throwable> predicate, T fallbackValue)`
        * `<E extends Throwable> Flux<T> onErrorReturn(Class<E> type, T fallbackValue)`
    * 에러 발생하면 다른 신호(시퀀스)나 다른 에러로 대체하기: onErrorResume
        * `Function<? super Throwable, ? extends Publisher<? extends T>> :`
    * 에러를 다른 에러로 변환하기: onErrorMap
    * 재시도하기: retry
    * 재시도하기: retryWhen
        * `retryWhen(Function< Flux<Throwable>,  ? extends Publisher<?> > whenFactory)`
        * whenFactory 함수에 전달되는 Flux<Throwable>은 원본 시퀀스의 익셉션과 연관되어 있으므로 이를 컴페니언(companion) Flux라고 부른다.
        * whenFactory 함수는 재시도 조건에 맞게 변환한 컴페니언 Flux를 리턴한다. 이 변환한 컴페니언 Flux가 재시도 여부를 결정하는데 그 과정은 다음과 같다.
            * 1. 에러가 발생할 때마다 에러가 컴페니언 Flux로 전달된다.
            * 2. 컴페니언 Flux가 뭐든 발생하면 재시도가 일어난다.
            * 3. 컴페니언 Flux가 종료되면 재시도를 하지 않고 원본 시퀀스 역시 종료된다.
            * 4. 컴페니언 Flux가 에러를 발생하면 재시도를 하지 않고 컴페니언 Flux가 발생한 에러를 전파한다.
* [스프링 리액터 시작하기 6 - 쓰레드 스케줄링](https://javacan.tistory.com/entry/Reactor-Start-6-Thread-Scheduling)
    * publishOn을 이용한 신호 처리 쓰레드 스케줄링
        * publishOn() 메서드를 이용하면 next, complete, error신호를 별도 쓰레드로 처리할 수 있다
        * ``` java
           Flux.range(1, 6)
           .publishOn(Schedulers.newElastic("PUB1"), 2)
           .map(i -> {
               logger.info("map 1: {} + 10", i);
               return i + 10;
           })
           .publishOn(Schedulers.newElastic("PUB2"))
           .map(i -> {
               logger.info("map 2: {} + 10", i);
               return i + 10;
           })
           .subscribe(new BaseSubscriber<Integer>() {
               @Override
               protected void hookOnSubscribe(Subscription subscription) {
                   logger.info("hookOnSubscribe");
                   requestUnbounded();
               }

               @Override
               protected void hookOnNext(Integer value) {
                   logger.info("hookOnNext: " + value);
               }

               @Override
               protected void hookOnComplete() {
                   logger.info("hookOnComplete");
                   latch.countDown();
               }
           });
           ```
             * publishOn()에 지정한 스케줄러는 다음 publishOn()을 설정할 때까지 적용
    * subscribeOn을 이용한 구독 처리 쓰레드 스케줄링
        * subscribeOn()을 사용하면 Subscriber가 시퀀스에 대한 request 신호를 별도 스케줄러로 처리한다.
        * ``` java
          CountDownLatch latch = new CountDownLatch(1);
          Flux.range(1, 6)
           .log() // 보다 상세한 로그 출력 위함
           .subscribeOn(Schedulers.newElastic("SUB"))
           .map(i -> {
               logger.info("map: {} + 10", i);
               return i + 10;
           })
           .subscribe(new BaseSubscriber<Integer>() {
               @Override
               protected void hookOnSubscribe(Subscription subscription) {
                   logger.info("hookOnSubscribe"); // main thread
                   request(1);
               }

               @Override
               protected void hookOnNext(Integer value) {
                   logger.info("hookOnNext: " + value); // SUB 쓰레드
                   request(1);
               }

               @Override
               protected void hookOnComplete() {
                   logger.info("hookOnComplete"); // SUB 쓰레드
                   latch.countDown();
               }
           });
          latch.await();
          ```
            * subscribeOn()으로 지정한 스케줄러는 시퀀스의 request 요청 처리뿐만 아니라 첫 번째 publishOn() 이전까지의 신호 처리를 실행한다. 따라서 위 코드를 실행하면 Flux.range()가 생성한 시퀀스의 신호 발생뿐만 아니라 map() 실행, Subscriber의 next, complete 신호 처리를 "SUB" 스케줄러가 실행한다.
    * subscribeOn() + publishOn() 조합
        * ``` java
          CountDownLatch latch = new CountDownLatch(1);
          Flux.range(1, 6)
                 .log()
                 .subscribeOn(Schedulers.newElastic("SUB"))
                 .map(i -> {
                     logger.info("map1: " + i + " --> " + (i + 20));
                     return i + 20;
                 })
                 .map(i -> {
                     logger.info("mapBySub: " + i + " --> " + (i + 100));
                     return i + 100;
                 })
                 .publishOn(Schedulers.newElastic("PUB1"), 2)
                 .map(i -> {
                     logger.info("mapByPub1: " + i + " --> " + (i + 1000));
                     return i + 1000;
                 })
                 .publishOn(Schedulers.newElastic("PUB2"), 2)
                 .subscribe(new BaseSubscriber<Integer>() {
                     @Override
                     protected void hookOnSubscribe(Subscription subscription) {
                         logger.info("hookOnSubscribe");
                         request(1);
                     }

                     @Override
                     protected void hookOnNext(Integer value) {
                         logger.info("hookOnNext: " + value);
                         request(1);
                     }

                     @Override
                     protected void hookOnComplete() {
                         logger.info("hookOnComplete");
                         latch.countDown();
                     }
                 });
          latch.await();
          ```
    * 실행결과
        * ![image](https://user-images.githubusercontent.com/20143765/79065892-a7f2f680-7cee-11ea-93d4-94d44e0ebacb.png)
    * 스케줄러 종류
        * Schedulers.immediate() : 현재 쓰레드에서 실행한다.
        * Schedulers.single() : 쓰레드가 한 개인 쓰레드 풀을 이용해서 실행한다. 즉 한 쓰레드를 공유한다.
        * Schedulers.elastic() : 쓰레드 풀을 이용해서 실행한다. 블로킹 IO를 리액터로 처리할 때 적합하다. 쓰레드가 필요하면 새로 생성하고 일정 시간(기본 60초) 이상 유휴 상태인 쓰레드는 제거한다. 데몬 쓰레드를 생성한다.
        * Schedulers.parallel() : 고정 크기 쓰레드 풀을 이용해서 실행한다. 병렬 작업에 적합하다.
        * 스레드풀 생성 메서드
            * newSingle(String name)
            * newSingle(String name, boolean daemon)
            * newElastic(String name)
            * newElastic(String name, int ttlSeconds)
            * newElastic(String name, int ttlSeconds, boolean daemon)
            * newParallel(String name)
            * newParallel(String name, int parallelism)
            * newParallel(String name, int parallelism, boolean daemon)
    * 일정 주기로 tick 발생: Flux.interval
* [스프링 리액터 시작하기 7 - 병렬 실행](https://javacan.tistory.com/entry/Reactor-Start-7-Parallel)
    * FLux parallel()과 runOn()으로 Flux 병렬 처리하기
    * Mono Mono.zip()으로 병렬 처리하기
        * Mono의 구독 처리 쓰레드를 병렬 스케줄러로 실행하고 Mono.zip() 메서드를 이용해서 Mono를 묶으면 각 Mono를 병렬로 처리
* [스프링 리액터 시작하기 8 - 모으기(aggregation)](https://javacan.tistory.com/entry/Reactor-Start-8-Aggregation)
    * List 콜렉션으로 모으기: collectList()
    * Map 콜렉션으로 모으기: collectMap()
    * Map의 값을 콜렉션으로 모으기: collectMultiMap()
    * 개수 새기: count()
    * 누적 하기: reduce()
    * 누적하면서 값 생성하기: scan()
        * 리턴 타입이 Flux인 것을 제외하면 reduce()와 동일
    * 데이터 조건 검사
        * all()이나 any()
* [스프링 리액터 시작하기 9 - 묶어서 처리하기(window buffer)](https://javacan.tistory.com/entry/Reactor-Start-9-window-buffer)
    * 일정 개수로 묶어서 Flux 만들기: window(int), window(int, int)
    * 일정 시간 간격으로 묶어서 Flux 만들기: window(Duration), window(Duration, Duration)
    * 특정 조건에 다다를 때가지 묶어서 Flux 만들기: windowUntil(Predicate)
    * 특정 조건을 충족하는 동안 묶어서 Flux 만들기: windowWhile(Predicate)
        *  해당 조건을 충족하지 않는 데이터가 나올 때까지 묶어서 Flux를 만든다. 조건을 충족하지 않는 데이터로 시작하거나 연속해서 데이터가 조건을 충족하지 않으면 빈 윈도우를 생성한다.
    * Flux 대신 List로 묶기: buffer류 메서드
        * window류 메서드가 Flux로 묶는다면 buffer류 메서드는 Collection으로 묶는다.
* [스프링 리액터 시작하기 10 - 로깅, 체크포인트](https://javacan.tistory.com/entry/Reactor-Start-10-logging-checkpoint)
    * 로깅: log()
        *  .log(null, Level.FINE) // java.util.logging.Level 타입
            * FINE은 DEBUG레벨
    * 체크포인트
        * 어떤 시점에 익셉션이 발생했는지 찾을때 도움
        ``` java
        Flux.just(1, 2, 4, -1, 5, 6)
               .map(x -> x + 1)
               .checkpoint("MAP1")
               .map(x -> 10 / x) // 원본 데이터가 -1인 경우 x는 0이 되어 익셉션이 발생
               .checkpoint("MAP2")
               .subscribe(
                       x -> System.out.println("next: " + x),
                       err -> err.printStackTrace());
        ```
---

