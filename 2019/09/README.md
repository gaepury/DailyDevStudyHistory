## 2019.09.02
- 프로세스와 스레드

## 2019.09.08
* [문서 엔지니어링과 API 문서화](https://engineering.linecorp.com/ko/blog/document-engineering-api-documentation/)
* Protocol Buffers Language Guide (휘리릭 읽는 프로토콜 버퍼 문법 및 작성 시 유의 사항, 이것만 알면 .proto 파일을 이해할 수 있다?)
    * 와닿지 않늗다..
* Spring boot Resttemplate 사용시 HttpComponentsClientHttpRequestFactory 옵션 설명(setConnectTimeout, setConnectionRequestTimeout, setReadTimeout)
    * 여러 set options들
* [(Troubleshooting) 레디스 사망일기](https://perfectacle.github.io/2019/05/29/redis-monitoring/)
* [JavaScript 배열(Array)의 발전과 성능에 대해서 자세히 알아보기](https://evan-moon.github.io/2019/06/15/diving-into-js-array/)
    * Javascript 배열
        * 같은타입의 배열을 사용해라(내부적으로 연속적인 메모리를 가진 배열로 변환). 그렇지 않으면 성능상으로 확연히 느려진다.
    * Typed Array
        * ArrayBuffers, Int8Array, Uint8Array, Uint8ClampedArray, Int16Array, Uint16Array, Int32Array, Uint32Array, Float32Array, Float64Array
* [지속 가능한 데이터 분석하기(지그재그)](https://brunch.co.kr/@zigzag/16)
    * 지그재그 회사 괜찮네..
* Kafka end Friends (ppt)
* [React + Storybook + puppeteer + jest 개발환경 구축하기](https://medium.com/@pitapat/3-react-storybook-puppeteer-jest-%EA%B0%9C%EB%B0%9C%ED%99%98%EA%B2%BD-%EA%B5%AC%EC%B6%95%ED%95%98%EA%B8%B0-85cc8be9b56c)
    * 코드, 에셋 변경에 대한 UI 영향도를 즉각적으로 확인
    * 실제 출력 결과를 비교하여 개발자에게 알려주므로 편리
* 파사드 패턴과 추상 팩토리 패턴
* CompletableFuture, parallelStream, ExecutorSev
* Docker 기반 분산 트랜스코더 개발
* [책 리뷰] 자바 최적화 (Optimizing Java,가장 빠른 성능을 구현하는 검증된 10가지 기법)
    * 사자
* Item 9. try-finally 보다 try-with-resources를 사용하라.
* [Docker 기반 분산 트랜스코더 개발](https://d2.naver.com/helloworld/3661677)
* [자바 Enum 실무에 적용 경험 공유하기 (properties에서 enum mapping, default value 사용하기)](https://jeong-pro.tistory.com/191)
* [AWS 자격증 시험 - 클라우드 종사자(Cloud Practitioner) 후기](AWS 자격증 시험 - 클라우드 종사자(Cloud Practitioner) 후기)
    * 용호님 글
* Elasticsearch 특정 형태소 종류를 제외하여 검색하는 필터 nori_part_of_speech 적용
* Elasticsearch nori 형태소 분석기에서 readingform filter를 이용해서 한자 내용을 한글로 변환하기
* Apollo Client는 Redux와 무엇이 다른가
    * Redux 단점
        * REST API를 사용하기 때문에 리소스의 크기가 서버에서 결정된다. 데이터 교환이 복잡하게 이루어지고, 엔드포인트 증가 및 overfetching과 underfetching 등의 문제점
* [Node.js] Redis로 캐싱 시스템 구축하기
* 5. 신입 개발자 면접 질문 모음 (클라우드, 인프라)
* [Spring에서 HMAC-SHA256 인증해보기](https://junebuug.github.io/2019-06-10/spring-hmac)
* 다시쓰는 Flask unittest (상,하편)
* [2019년과 이후 JavaScript의 동향 - JavaScript(ECMAScript)](https://d2.naver.com/helloworld/4007447)
* [[번역] Elasticsearch 퍼포먼스 튜닝 방법 - ebay](https://wedul.site/613)
    * 1. 쿼리에 filter가 들어가고 그 값이 Enumerable할 때는 인덱스를 나눠서 설계하라
    * 2. 값이 enumerable하지 않다면 routing key를 사용하라.
    * 3. 기간이 정해져 있는 데이터들의 경우 기간별로 인덱스를 구성하여 사용하라.
    * 4. mapping을 효율적으로 지정하라(자동 mapping 지양)
    * 5. 사용자 정의 id를 사용할 경우 불균형 샤딩에 대해 조심하라.
    * 6. 여러 노드에 고르게 shard를 만들어라.
    * 7. bulk request를 높이고 refresh 기간을 올려라.
    * 8. replica 수를 줄여라.
    * 9. 가능하면 자동으로 생성되는 ID를 사용하라.
    * 10. 가능하면 query context에 filter를 사용해라.
    * 11. shard 노드를 효율적으로 관리하라
    * 12. stop word를 사용한 검색을 자제하라
* Elasticsearch에서 reindex를 이용해서 매핑정보 변경하기
* Elasticsearch template를 일별 index 구성하기
* LRU Cache Algorithm 정리
* Elasticsearch에서 Dictionary 변경 시 analyzer와 인덱싱된 Document 갱신 방법
* 스트레티지 패턴 
* 옵저버 패턴
* 데코레이터 패선
    * ex: Java I.O의 inputstream
* 싱글턴 패턴
* 함수형 프로그래밍 정리
* 쿠버네티스 패키지 매니저 Helm
* Docker Best Practices
* [React, Typescript, Webpack환경에서 번들링 속도 올리기](https://b.luavis.kr/web/speed-up-webpack)
* Python 로그를 남기는 Logbook 라이브러리 알아보기
* 고객 행동 기반 실시간 딥 뉴럴 추천 시스템 : ForYou
* 주니어 개발자가 반응형 레이아웃 리팩토링한 썰.txt


## 2019.09.14
* 레거시 코드에서 이해하기 쉬운코드로 리팩토링
* 워드프레스 아임포트 결제 플러그인 다중 정기결제(multiple subscription) 업데이트 
* LINE Search UI 개선기
* 쉽게 설명한 LSH-Minhash 알고리즘
    * 모르겠다~
* 50. [Kubernetes] IPVS, iptables, userspace - 네트워크 종류에 따른 패킷의 흐름
    * https://ssup2.github.io/theory_analysis/Kubernetes_Service_Proxy/
        * 먼소린지 하나도 모르겠네.. 
        * 나중에 더 공부하고 다시 봐보자
* [PM2를 활용한 Node.js 무중단 서비스하기](https://engineering.linecorp.com/ko/blog/pm2-nodejs/)
* Berlekamp-Massey 알고리즘
    * 모르겠다..
* Facebook F8 2019 후기 #1, Facebook F8 2019 후기 #2
* 디자인패턴8-전략 패턴/스트래티지 패턴(Strategy Pattern)
* Python 문자열 해싱하여 아바타 사진 생성하는 pagan 라이브러리 알아보기
* HTTP/2 성능 향상을 위한 NGINX 구조 개선
    * https://blog.cloudflare.com/ko/nginx-structural-enhancements-for-http-2-performance-ko/
    * 너무어려워
* Spring layered architecture와 객체지향적으로 개발하기
* [Spring AOP 의 개념과 이해](https://jins-dev.tistory.com/entry/Spring-AOP-%EC%9D%98-%EA%B0%9C%EB%85%90%EA%B3%BC-%EC%9D%B4%ED%95%B4)
   * Aspect : 핵심기능에 부가될 수 있는 모듈을 말한다. 재사용 가능하며 핵심적인 기능에 부가되어 의미를 가질 수 있는 모듈이다.
   * Advice : Aspect 에 대한 구현체가 된다. 주로 어느시점에 어떤 동작을 할지가 기술된다.
   * Point Cut : 핵심 모듈을 분리할 선이자, 어드바이스를 적용할 시점(Join Point)을 정의하는 모듈이 된다.
   * Proxy : 타겟은 프록시를 통해 호출되며 타겟 메서드 실행에 대한 전처리 후처리를 담당해줌과 동시에 AOP 추상화에 있어서 인터페이스를 제공한다.
   * Weaving : 핵심 로직 코드에의 적용을 말하며, Aspect 가 적용됨으로써 새로운 Proxy 객체가 생성된다.
   * Cross Cut : 공통 로직을 비즈니스 로직에서 추출해내는 것을 Cross Cutting 이라 한다.
   * Scaling 의 종류에 대한 정리
* [[Python] 잘 알려져 있지 않은 파이썬 기능](https://yuda.dev/254)
* [[번역] Linux에서 메모리를 다 써버렸을 때 일어나는 일](https://www.google.com/search?q=%5B%EB%B2%88%EC%97%AD%5D+Linux%EC%97%90%EC%84%9C+%EB%A9%94%EB%AA%A8%EB%A6%AC%EB%A5%BC+%EB%8B%A4+%EC%8D%A8%EB%B2%84%EB%A0%B8%EC%9D%84+%EB%95%8C+%EC%9D%BC%EC%96%B4%EB%82%98%EB%8A%94+%EC%9D%BC&oq=%5B%EB%B2%88%EC%97%AD%5D+Linux%EC%97%90%EC%84%9C+%EB%A9%94%EB%AA%A8%EB%A6%AC%EB%A5%BC+%EB%8B%A4+%EC%8D%A8%EB%B2%84%EB%A0%B8%EC%9D%84+%EB%95%8C+%EC%9D%BC%EC%96%B4%EB%82%98%EB%8A%94+%EC%9D%BC&aqs=chrome..69i57.208j0j4&sourceid=chrome&ie=UTF-8)
    * free 출력
    * vmstat 출력
    * dmesg(운영체제 로그)
* Protocol Buffers - overview
* Protocol Buffer 원리로 배우는 고성능 직렬화, 역직렬화 전략! Protocol Buffer 예제 테스트(구글이 쓰는 이유가 있었네)
* 딥러닝 추천 시스템 in production
* 딥러닝을 활용한 거래량 예측 기능 개선
* Annotation과 Reflection을 이용한 챗봇 컨트롤러 만들기
    * Annotation, reflections 사용
* [캐시가 동작하는 아주 구체적인 원리](https://parksb.github.io/article/29.html)
    * 어렵다ㅠ
* [[번역] 파이썬 매직 메소드 (Python's Magic Methods)](https://ziwon.dev/post/python_magic_methods/)

## 2019.09.15
* tcpdump
* [docker] 도커 네트워크(bridge)를 생성하는 예시
* 05 - Flex Panel Gallery
* [[번역] Redis partitioning](https://wedul.site/584)       
    * redis의 경우 싱글 스레드로 돌아가기 때문에 작업이 오래 발생되는 keys나 flushall은 사용하지 말아라. 1만건 이하에 데이터를 조작하는 경우에는 사용해도 되는데 그 이상 사용하는 경우에는 주의하라는 뜻.
* 디자인 패턴3 - 데코레이터 패턴
* 디자인 패턴4 - 템플릿 메소드 패턴이란(Template method pattern)
* 디자인패턴5 - 컴포지트 패턴 (Composite pattern )
* 디자인 패턴6 - 옵저버 패턴(Observer pattern)
* 스프링 프록시 패턴 - Proxy Pattern
* Let’s talk about data structures in Python
* [How to Test Your Vue Project with Jest and Nightwatch](https://hashnode.com/post/how-to-test-your-vue-project-with-jest-and-nightwatch-cjskmturk00665ss1gauawb84)
    * nightwatch 약간 푸피터와 비슷한 느낌인데?
* Understanding Python slices
* Enforcing Single Responsibility Principle in Python
* 알아두면 좋은 MySQL 설정들
* [AWS 서비스를 활용한 Kubernetes 클러스터 구축](http://engineering.vcnc.co.kr/2019/03/kubernetes-on-aws/)
    * 서비스를 외부에 노출: NGINX Ingress Controller + NLB
    * Pod에 IAM 역할 부여: kube2iam¶
    * 로그 수집: fluentd + CloudWatch Logs¶
    * 모니터링: Prometheus¶
    * 자동 처리량 확장: Cluster Autoscaler¶
* [progressive react](https://houssein.me/progressive-react)
    * Measure component-level rendering performance with either of the following:
        * Chrome DevTools Performance panel
        * React DevTools profiler
    * Minimize unecessary component re-renders
        * Override shouldComponentUpdate where applicable
        * Use PureComponent for class components
        * Use React.memo for functional components
        * Memoize Redux selectors (with reselect for example)
        * Virtualize super long lists (with react-window for example)
    * Measure app-level performance with Lighthouse
    * Improve app-level performance
        * If you are not server-side rendering, split components with React.lazy
        * If you are server-side rendering, split components with a library like loadable-components
        * Use a service worker to cache files that are worth caching. Workbox will make your life easier.
        * If you are server-side rendering, use streams instead of strings (with renderToNodeStream and renderToStaticNodeStream)
        * Can't SSR? Pre-render instead. Libraries like react-snap can help.
        * Extract critical styles if you are using a CSS-in-JS library.
        * Make sure your application is accessible. Consider using libraries like React A11y and react-axe.
        * Add a web app manifest if you think users would like to access your site through their device homescreen.
* [쿠버네티스 pod 구성 패턴](https://arisu1000.tistory.com/27863)
    * 사이드카 패턴(Sidecar)
    * 앰배서더 패턴(Ambassador)
    * 어댑터 패턴(Adapter)
* [NodeJS에서 async_hooks을 이용해 요청의 고유한 context 사용하기](https://tech.ssut.me/getting-per-request-context-in-nodejs-with-async_hooks/)
* [최신 브라우저의 내부 살펴보기 1 - CPU, GPU, 메모리 그리고 다중 프로세스 아키텍처](https://d2.naver.com/helloworld/2922312)
* [최신 브라우저의 내부 살펴보기 2 - 내비게이션 과정에서 일어나는 일](https://d2.naver.com/helloworld/9274593)
* [최신 브라우저의 내부 살펴보기 3 - 렌더러 프로세스의 내부 동작](https://d2.naver.com/helloworld/5237120)
* [최신 브라우저의 내부 살펴보기 4 - 컴포지터가 사용자 입력을 받았을 때](https://d2.naver.com/helloworld/6204533)
* [Java] Jsoup 크롤링 및 파싱 - text 줄바꿈 사라짐
* [Redux-Saga 소개](https://blog.javarouka.me/2019/04/02/redux-saga-1/)
   * ![image](https://user-images.githubusercontent.com/20143765/66271262-f3879c00-e896-11e9-8cad-8dccb9267e89.png)
      * 특정 END시점에 호출(연결)되게 할수도 있다. 신박하다
   * select
      * ![image](https://user-images.githubusercontent.com/20143765/66271273-069a6c00-e897-11e9-8e54-12f18c56e78b.png)
         *  인자로 셀렉터(함수)를 줄 수 있다.
* [Springboot hystrix 사용기 (hystrix로 마이크로 서비스 간의 서비스 호출 실패를 방지해보자)](https://jeong-pro.tistory.com/183)
* [11번가 Spring Cloud 기반 MSA로의 전환 - 발표정리](https://happyer16.tistory.com/entry/11%EB%B2%88%EA%B0%80-Spring-Cloud-%EA%B8%B0%EB%B0%98-MSA%EB%A1%9C%EC%9D%98-%EC%A0%84%ED%99%98-%EB%B0%9C%ED%91%9C%EC%A0%95%EB%A6%AC)
    * CommandKey 단위로 통계를 내고 동작한다. 그렇다면 같은 한 CommandKey에서 서킷 오픈되면 같은 ComandKey를 가진 모들 메서드들은 서킷 오픈되는거아냐?
* 172. [Kubernetes] Admission Controller의 이해 및 Python으로 Mutate Webhook 작성 예제
* 정적 사이트 생성기 Gatsby
* 도커 & 쿠버네티스 8,9주차 스터디
* HTTP 요청에 body를 붙여서 보내면 어떤 일이 벌어질까? part 2
* 시스템 행 현상이 발생되었을 때 NMI를 이용한 덤프 분석
* 만화로 나누는 자유/오픈소스 소30. 리눅스 이야기: 리눅스 vs. 미닉스 1,2부
* Spring Boot에서 6.4 Elasticsearch 연결 및 간단 CRUD
* [React - React Concurrent Mode](https://ideveloper2.tistory.com/170)
* [번역] shared message queues와 publish-subscribe 방식에 Custom Group 방식을 더한 Kafka 소개
* RabbitMQ에 대해

## 2019.09.21
* HTTPS/DNS 차단 쉽게 이해하기
* Introducing React Hooks
* Spring Guide - 테스트 전략
* [소프트웨어 공학 - Observer Pattern]
