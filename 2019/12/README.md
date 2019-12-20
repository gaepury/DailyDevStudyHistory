## 2019.12.02
* [React Hook 정리](https://velog.io/@noyo0123/React-Hook-%EC%A0%95%EB%A6%AC)
   * useState
      * state get, set
   * useEffect
      * componentDidMount와 componentDidUpdate를 대체
* [Outsider 기술 뉴스 #138 : 19-12-02](https://blog.outsider.ne.kr/1467)

## 2019.12.04
* [SpringBoot Application의 monitoring 시스템 구축하기](https://jongmin92.github.io/2019/12/04/Spring/prometheus/)
    * Dependency 설정
        * ![image](https://user-images.githubusercontent.com/20143765/70228476-c3298480-1797-11ea-8b72-b7b94a2fa382.png)
    * Actuator web expose endpoint에 prometheus 추가
## 2019.12.05
- [Spring Boot에서 테스트를 - 1](https://hyper-cube.io/2017/08/06/spring-boot-test-1/)
  - spring-boot-test 포함 라이브러리 
     - JUnit
     - Spring Test & Spring Boot Test
     - AssertJ
     - Hamcrest
     - Mockito
     - JSONassert
     - JsonPath
  - @SpringBootTest 어노테이션
     - ApplicationContext를 쉽게 생성하고 조작, 기존 spring-test에서 사용하던 @ContextConfiguration의 발전된 기능
     - @RunWith(SpringRunner.class)와 함께 사용
  - Bean
     - @SpringBootTest classes 속성을 이용하여 손쉽게 빈 등록
     - ![image](https://user-images.githubusercontent.com/20143765/71225508-34327580-231c-11ea-877c-19c74281a79d.png)
  - TestConfiguration
     - 기존에 정의했던 Configuration을 커스터마이징하고 싶은 경우 TestConfiguration 기능을 사용. TestConfiguration은 ComponentScan 과정에서 생성될 것이며 해당 자신이 속한 테스트가 실행될때 정의된 빈을 생성하여 등록할 것
     - 더 좋은 방법은 @Import 어노테이션을 사용하는 것. @Import 어노테이션을 통해서 직접 사용할 TestConfiguration을 명시
       - ![image](https://user-images.githubusercontent.com/20143765/70228639-03890280-1798-11ea-8d26-258167842c85.png)
  - MockBean and SpyBean
     - spring-boot-test 패키지는 Mockito를 포함
  - Properties
    - properties 속성
    - 별도의 테스트를 위한 application.properties(또는 application.yml)을 지정(vm옵션도 지정가능)
  - Web Environment test
     - @SpringBootTest의 webEnvironment 파라미터를 이용
     - MOCK, RANDOM_PORT< DEFINED_PORT, NONE
  - TestRestTemplate
     - MovcMvc와 차이: Servlet Container를 사용하느냐 안하느냐의 차이. MockMvc는 Servlet Container를 생성하지 않는다.. 반면, @SpringBootTest와 TestRestTemplate은 Servlet Container를 사용한다.
  - 트랜젝션   
     - RANDOM_PORT나 DEFINED_PORT로 테스트를 설정하면 실제 테스트 서버는 별도의 스레드에서 수행되기 때문에 rollback이 이루어지지 않는다.
  - ApplicationContext 캐시
     -  동일한 ApplicationContext 사용
## 2019.12.14
* [Enum 찾기의 달인 (효율적으로 찾기, spring bean과 맵핑)](https://sjh836.tistory.com/175)
    * 1. Enum을 효율적으로 찾는 방법
       * ``` java
         public static final Map<String, OperatingSystemType> map = new HashMap<>(); 
         static { for (OperatingSystemType os : OperatingSystemType.values()) { map.put(os.getCode(), os); } }
         public static OperatingSystemType getOs3ByCode(String code) { return map.get(code); }
         ```
    * 2. Enum 으로 Bean 을 찾아보자
       * EnumMap 으로 enum 과 bean 을 바로 맵핑
         ``` java
         Map<OperatingSystemType, OperatingSystemHandler> map = new EnumMap<>(OperatingSystemType.class); 
         // OperatingSystemHandler 구현체에서 enum type 을 getType 메소드로 명시 
         for (OperatingSystemHandler handler :
         operatingSystemHandlerList) { map.put(handler.getType(), handler); }
         ```

## 2019.12.19
* [자바스크립트 - 가비지 컬렉터](https://velog.io/@pa324/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EA%B0%80%EB%B9%84%EC%A7%80-%EC%BB%AC%EB%A0%89%ED%84%B0)
   * 클로저에 의해 메모리 누수가 발생할 수 있다.
* [잘못 된 문서화, 잘 된 문서화](https://tech.peoplefund.co.kr/2019/12/06/bad-and-good-documentation.html)
   > 엔지니어는 문제를 해결하는 사람이지 주의 사항을 알리는 사람이 아니기 때문입니다. 도로에 구멍이 났을 때 엔지니어의 역할은 그 구멍을 메우고 다시 나지 않게 하는 것이지, “여기 구멍이 있으니 아무도 지나가지 마!” 라고 외치는 것이 아닙니다.
* [기술 뉴스 #140 : 19-12-16](https://blog.outsider.ne.kr/1471?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+rss_outsider_dev+%28Outsider%27s+Dev+Story%29)
* [크로스 웹 브라우저 테스트 툴](https://www.mrlatte.net/research/2019/12/08/cross-web-browser-test-tool.html)
   * Browserstack, LambdaTest, CrossBrowserTesting, Browserling, Experitest, Functionize, Saucelabs, EndTest, Selenium, IE Tab
* [What's New for Node.js in 2020](https://developer.okta.com/blog/2019/12/04/whats-new-nodejs-2020#internationalization-support-expands-in-2020)
    * Support for ECMAScript Modules: you can finally use import and export syntax you may already be using for client-side JavaScript running in the browser.
    * Node.js can Import WebAssembly Modules
    * Internationalization Support Expands in 2020
    * QUIC protocol support: a modern transport for connected applications with increased performance and reliability.
    * Better Python 3 build support: in 2020 it should be possible to build Node.js and native modules using Python 3.
    * An Updated V8 JavaScript engine: V8 v7.8 and 7.9 increase performance and Wasm support.
    * Stable Workers Threads API

## 2019.12.20
* [JAVA ConcurrentHashMap](https://dydtjr1128.github.io/java/2019/12/18/JAVA-ConcurrentHashMap.html)
    * 하나의 공유자원을 여러개의 세그먼트로 나누고 각 세그먼트별로 다른 락을 거는 기법을lock striping이라고 부르는데, 이 기법을 적용시킨 ConcurrentHashMap은 기본적으로 16개의 세그먼트로 나뉘어져 있고, 각 세그먼트별로 다른 lock으로 동기화 되도록 만들었다.
    *  ConcurrentHashMap과 Collections.synchronizedMap(new HashMap<>())의 성능을 비교
       * ![image](https://user-images.githubusercontent.com/20143765/71225475-1b29c480-231c-11ea-9016-67589202c170.png)
* [docker 명령어 정리](https://velog.io/@pa324/docker-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%A0%95%EB%A6%AC)
    * Docker 컨테이너 Timezone 변경(Dockerfile에서 local서버 시간과 동기화)
      * ```
        ENV TZ=Asia/Seoul
        RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
        ```
