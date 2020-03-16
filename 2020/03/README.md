## 2020.03.09(3개)
* [Outsider`s 기술 뉴스 #145 : 20-03-02](https://blog.outsider.ne.kr/1478?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+rss_outsider_dev+%28Outsider%27s+Dev+Story%29)
  * [Redux template for Create-React-App](https://github.com/reduxjs/cra-template-redux/releases/tag/v1.0.0)
     
* [테스트 커버리지 100%](https://blog.npcode.com/2020/02/28/%ed%85%8c%ec%8a%a4%ed%8a%b8-%ec%bb%a4%eb%b2%84%eb%a6%ac%ec%a7%80-100/)
  * jacoco
      * Docs
          * https://www.jacoco.org/jacoco/trunk/doc/
      * The JaCoCo Plugin
          * https://docs.gradle.org/current/userguide/jacoco_plugin.html
      * Gradle 프로젝트에 JaCoCo 설정하기
          * https://woowabros.github.io/experience/2020/02/02/jacoco-config-on-gradle-project.html
* [What’s New in Java 14?](https://medium.com/better-programming/whats-new-in-java-14-a472ec291c05)
  * Switch Expressions
      * ![image](https://user-images.githubusercontent.com/20143765/76228325-eca8ef00-6263-11ea-8598-ef6752465b45.png)
      * Multi line block + yield
          * ![image](https://user-images.githubusercontent.com/20143765/76228346-f3376680-6263-11ea-8e1b-21e9016a1805.png)
              * yield
                  * 14부턴 키워드로 생각
  * Helpful NullPointerExceptions
      * NullpointerException 설명 디테일 추가
  * Better Garbage Collection
      * ZGC
          * macOS, window에 추가(기존엔 Linux에서만 사용가능)
          * ZGC는 가비지 콜렉션의 일시 정지 시간을 줄이고 수백 메가 바이트에서 수 테라 바이트에 이르는 크기의 힙을 처리 할 수 있다.
      * CMS
          * Good Bye
      * Parallel Scavenge 및 Serial Old Garbage Collection 알고리즘의 조합을 더 이상 사용하지 않습니다.
          * XX:UseParallelOldGC deprecate
  * Language preview features
      * 바인딩 변수를 사용하여 instanceof 연산자를 extend
          * ![image](https://user-images.githubusercontent.com/20143765/76228341-efa3df80-6263-11ea-89a9-1038554d20e7.png)

---

## 2020.03.12(2개)
* [(Spring Boot)오류 처리에 대해](https://supawer0728.github.io/2019/04/04/spring-error-handling/)
    * Spring Boot의 기본 오류 처리 - BasicErrorController
        * AbstractErrorController를 상속
        * BasicErrorController에서는 HTML 요청, 그 외의 요청을 나누어서 처리할 핸들러를 등록하고 getErrorAttributes를 통해 응답을 위한 모델을 생성
        * ![image](https://user-images.githubusercontent.com/20143765/76483108-84bbf980-6459-11ea-81b7-cfed776d7e9d.png)
    * Spring Boot의 기본 오류 처리 - AbstractErrorController와 ErrorAttributes
        * BasicErrorController의 getErrorAttributes 메서드를 깊게 봐보자
            * getErrorAttributes메서드는 상위클래스인 AbstractErrorController에 구현
                * ![image](https://user-images.githubusercontent.com/20143765/76483115-87b6ea00-6459-11ea-80be-6360afe05364.png)
                * ErrorAttributes 인터페이스의 getErrorAttributes를 호출(위임자 패턴)
                * 별도로 ErrorAttributes를 등록하지 않았다면 Spring Boot는 DefaultErrorAttributes를 사용
                * DefaultErrorAttributes
                    * ![image](https://user-images.githubusercontent.com/20143765/76483119-8be30780-6459-11ea-9534-aba8d9a0f4d7.png)
                        * timestamp, status, detail, path 매핑
                    * ErrorAttributes에서 가져온 모델로 응답을 생성
                    * ![image](https://user-images.githubusercontent.com/20143765/76483125-8f768e80-6459-11ea-8b9b-d44ab311cba9.png)
    * 확장 포인트 - ErrorAttributes
        * ![image](https://user-images.githubusercontent.com/20143765/76483133-92717f00-6459-11ea-9731-b1139ccb3022.png)
    * HTML View 연계 - 404.html, 4xx.html
        * 기본 경로 하위에 /error/{응답코드}로 view의 이름을 작성하는 경우 ErrorController에서 응답 코드에 맞게 해당 view로 응답을 내려준다.
    * View를 가져오는 방법 - TemplateAvailabilityProvider
    * 확장 포인트 - BasicErrorController
        * 로그 추가하기
        * ![image](https://user-images.githubusercontent.com/20143765/76483141-96050600-6459-11ea-93ef-7188735bc0b0.png)
    * ErrorController에 대한 추가 설명
        * flow
            * 1. 서블릿 컨테이너(ex: 톰캣)에서 등록된 서블릿에서 요청을 처리하다가
            * 2. 오류가 발생했는데
            * 3. 해당 서블릿에서 처리하지 못하고
            * 4. 서블릿 컨테이너까지 오류가 전파되었을 때, 서블릿 컨테이너가 오류를 처리하기 위해 특정 경로(server.error.path)로 해당 요청처리를 위임할 때 사용된다.
            * ![image](https://user-images.githubusercontent.com/20143765/76483147-98fff680-6459-11ea-90f9-2c9ac5d846c7.png)
                * 앞의 추가 설명에서 봤듯이 ErrorController가 동작하는 것은 요청을 처리해야할 Servlet에서 오류가 발생했으나 해당 Servlet에서 오류를 처리하지 않아서 Servlet Container까지 오류가 전파되었을 때(ServletException으로 래핑된다), Servlet Container가 ErrorController를 호출한다. 
    * spring-mvc Exception 기반으로 오류 처리
        * 위와 같은 과정을 @ExceptionHandler + @ControllerAdvice 로 처리가능
        * ![image](https://user-images.githubusercontent.com/20143765/76483157-9c937d80-6459-11ea-91d2-40797109f39d.png)
* [Node CPU 점유율 최적화 경험기](https://hyperconnect.github.io/2020/02/11/Node-cpu-debug.html)
  * Node Profiling
      * node --prof index.js
  * 벤치마킹
      *  ab -k -c 50 -n 10000 "http://localhost:3000"
  * Visualize CPU Usage
      * Sunburst Graph나 Flame Graph를 주로 사용
          * ![image](https://user-images.githubusercontent.com/20143765/76538324-7b1aac00-64c2-11ea-965b-72e232c8c30c.png)
      * flamebearer 사용하여 프로파일링 로그를 Flame Graph로 그리기
          * $ npm install -g flamebearer # flamebearer 설치
          * $ node --prof-process --preprocess -j isolate*.log | flamebearer # 프로파일링 로그로 Flame graph 생성
  * CPU 점유율 개선하기
      * request마다 실행되던 i18next 클래스를 initialize 하는 함수를 singletone기반으로 변경

---

## 2020.03.13(1개)
* [emotion을 활용한 크몽 프론트엔드 스타일링 시스템](https://brunch.co.kr/@kmongdev/17?fbclid=IwAR2tG_iLC1G4xA5dIf0FG_9KMhOfD9Lm-UBFsbzr5wWH6ktLd_91ysMlS44)
    * Sass
        * 중첩, 상위 선택자 참조등 편리한 문법, 변수, 함수, 상속등의 기능을 이용
    * CSS Module
        * 컴포넌트 단위로 캡슐화 
    * CSS관리의 어려움
        * Global Namespace
        * Dependencies
        * Dead Code Elimination
        * Minification
        * Sharing Constants
        * Non-deterministic Resolution
        * Isolation
    * CSS IN JS
        * emotion
            * 특별한 기능이 없는 UI에 클래스 이름을 지어야하는 경우 emotion의 인라인 스타일로 해결 및 컴포넌트에 적용된 스타일 코드를 찾아다닐필요 없이 바로 확인 가능
        * styled componets
        
---

## 2020.03.13(2개)
 * [REST API를 버리고 Graph QL를 선택한 이유? (Why GraphQL is the future)](https://www.youtube.com/watch?v=1imQ1_aOQvU)
    * Rest API보다 GraphQL 훨빠름. 코드도 훨 예쁨
    * 리액트와 호환성이 쩔음, 라이브러리, 커뮤니티 지원도 있고 query만 만들면 됨
    * 리덕스 대체 가능 with GraphQL + Apool로 조합
* [웹 어셈블리는 자바스크립트의 무덤일까?](https://www.youtube.com/watch?v=KjgDxBLv0bM)
    * Go , rust등으로 웹어셈블리로 컴파일, 웹어셈블리(바이너리 파일)을 브라우저에서 읽을수 있음
    * ![image](https://user-images.githubusercontent.com/20143765/76697795-02446b80-66df-11ea-967e-b00bf109c84f.png)
    * 웹어셈블리와 자바스크립트는 공존 가능
        * 자바스크립트는 화려한 웹, 인터렉티브
        * 웹어셈블리는 이미지 프로세싱등 리얼타임 작업
 * [알아두면 유익한 2019 개발이야기](https://subicura.com/2020/01/07/2019-dev-summary.html?fbclid=IwAR06K4AvlHIX3nMh1D02Egqy_jVT6N7zgPteBhhJUfnrB0XtN7G9FHtiETA)
     * 타입스크립트
     * ESLint+Prettier
     * Jest & Enzyme로 React 테스트하기(스냅샷 테스팅)
     * Styled Component
     * Atomic Design
         * ![image](https://user-images.githubusercontent.com/20143765/76706678-bcae8f80-672c-11ea-91bb-7fd48d2e11c3.png)
     * Storybook - 공통 컴포넌트 개발환경
     * Ant Design - 어드민을 위한 React 프레임워크
     * Next.js
     * GraphQL(feat. hasura) 도입
     * Apollo - 최고의 GraphQL 라이브러리
         * Apollo Client
         * Apollo Server
         * Apollo Graph Manager
     * 정적페이지 만들기 - HTML의 귀환
         * Jamstack
     * Cloud Run - 가장 쉬운 컨테이너 배포 방법
       * Cloud Run 배포하기
           * Cloud Source Repository
               * Git 저장소인데 뭔가 구글스러운(안 이쁜) UI
               * 메인 저장소가 아니라 배포를 위한 저장소로 사용
                 * origin - 기존 git 원격 저장소
                 * google - cloud source repository
           * Google Cloud Build
               * Cloud Source Repository에 소스가 푸시되면 트리거 발생
               * Dockerfile이 있으면 모든 게 자동화 - Commit ID로 도커 이미지를 빌드하고 Container Registry에 이미지를 저장
           * Cloud Run
               * 애플리케이션을 만들 때 Container Regsitry에 등록된 이미지를 선택
               * 커스텀 도메인 연결은 도메인 관리자에서 CNAME만 추가하면 됨
               * Google Cloud SQL(MySQL) 연동 가능
               * HTTPS 기본 지원
               * 사용한 만큼만 비용 발생
     * Kubernetes - EKS 도입
     * Terraform

--- 
## 2020.03.16(2개)
 * [넷플릭스 성능 케이스스터디](https://kyu.io/%eb%84%b7%ed%94%8c%eb%a6%ad%ec%8a%a4-%ec%84%b1%eb%8a%a5-%ec%bc%80%ec%9d%b4%ec%8a%a4%ec%8a%a4%ed%84%b0%eb%94%94/#utm_source=rss&utm_medium=rss&utm_campaign=%25eb%2584%25b7%25ed%2594%258c%25eb%25a6%25ad%25ec%258a%25a4-%25ec%2584%25b1%25eb%258a%25a5-%25ec%25bc%2580%25ec%259d%25b4%25ec%258a%25a4%25ec%258a%25a4%25ed%2584%25b0%25eb%2594%2594)
     * 자바스크립트를 더 적게 만들어 Time-to-Interactive 줄이기(React 제거)
         * 첫 입력 지연(First Input Delay)이 빠르다
             * 첫 입력 지연이란 사용자가 첫 동작을 시작한 순간부터 브라우저가 그 동작에 응답한 순간까지를 뜻한다.
     * 이어지는 페이지에서 사용되는 React 미리 가져오기(Prefetch)
     * 결론
         * 리소르를 미리 가져오고 홈페이지의 클라이언트 코드를 최적화하여, 가입 과정의 Time-to-Interactive 매트릭스를 크게 개선 할 수 있었다. 브라우저에 포함된 API(link)와 XHR을 이용해 곧 방문할 페이지들을 미리 가져옴으로써, Time-to-Interactive를 30% 감소 시킬 수 있었다.
     * 추가 성능 측정 도구들
         * https://developers.google.com/web/fundamentals/performance/speed-tools/
 * [(번역) 시작해요, 런타임 성능 분석!](https://yobi.navercorp.com/common_share/posts/1252)
     * Performance 탭
         * FPS, CPU, NET
         * Network
         * Frames
         * interactions
         * Timing
             * FP(First Paint)
             * FCP(First Contentful Paint)
             * FMP(First Meaningful Paint)
             - DCL(DOMContentLoaded Event)
                - 렌더링의 과정중에 우리가 javascript등으로 DOM 컨트롤을 시작할수있는 부분은 DCL부터 
                - HTML과 CSS에 대한 파싱이 끝나는 시점
                - 렌더트리를 구축할 준비가 된 (DOM과 CSSOM이 완료된) 상황
                - 제이쿼리 기준 - $(document).ready(…) 시점
             - LCP(Largest Contentful Paint)
             - L(Onload Event)
                - HTML 상에 필요한 모든 리소스가 로드된 시점
                - 제이쿼리 기준 - $(window).load(…)시점
         * Main
* [성능 최적화(NHN TOAST UI)](https://ui.toast.com/fe-guide/ko_PERFORMANCE/#%EB%A6%AC%EC%86%8C%EC%8A%A4-%EC%9A%A9%EB%9F%89-%EC%A4%84%EC%9D%B4%EA%B8%B0)
    * 성능 최적화에 필요한 이론과 측정 도구
        * 레이아웃(리플로우)과 리페인트
            * 브라우저 로딩 과정 중 스타일 이후의 과정(스타일 -> 레이아웃 -> 페인트 -> 합성)을 렌더링이라고 하는데, 이 렌더링 과정은 상황에 따라 반복하여 발생할 수 있다. 스타일 단계에서 구성되는 렌더 트리는 자바스크립트에 의해 DOM 트리, CSSOM 트리가 변경될 때 다시 재구성된다. DOM이 추가/삭제되거나 요소에 기하적인 영향(높이, 넓이, 위치)을 주는 CSS 속성값을 변경하는 경우, 렌더 트리가 다시 재구성된다. 즉, 레이아웃부터 이후 과정을 다시 수행하며 이것을 레이아웃이라고 한다(또는 리플로우라고도 한다).
                * ![image](https://user-images.githubusercontent.com/20143765/76754046-d3a0c080-67c4-11ea-93bf-6443f1fc1f9f.png)
            * 레이아웃은 요소에 기하적인 영향을 주는 CSS 속성값을 변경할 때 발생한다고 하였는데, 반대로 영향을 주지 않는 CSS 속성값을 변경하면 레이아웃 과정을 건너뛴다. 페인트부터 수행하며 이를 리페인트라고 한다.
                * ![image](https://user-images.githubusercontent.com/20143765/76754040-d0a5d000-67c4-11ea-9ad0-e05c8639a79f.png)
            * 레이아웃이 일어나면 전체 픽셀을 다시 계산해야 하므로 부하가 크다. 반면 리페인트는 이미 계산된 픽셀값을 이용해 화면을 그리기 때문에 레이아웃에 비해 부하가 적다. 다음은 어떤 엘리먼트에 레이아웃과 리페인트를 발생시키는 CSS 속성과 해당 속성값을 변경했을 때 차이를 보여준다.
            * 레이아웃과 리페인트를 발생시키는 CSS 속성 목록: http://goo.gl/lPVJY6
        * 블록 리소스와 주요 렌더링 경로
            * 브라우저 로딩 초기 단계에서 HTML 파싱이 일어날 때 CSS 또는 자바스크립트로 인해 파싱이 중단될 수 있다. 이렇게 파싱이 중단되는 상황을 HTML 파싱이 블록되었다라고 표현하며, 블록 상태의 원인이 되는 리소스를 블록 리소스(Block resource)
            * 구글에서는 주요 렌더링 경로(Critical Rendering Path)를 최적화하면 페인팅을 빠르게 하고 로딩 속도를 개선할 수 있다고 설명
        * 성능 개선 지표
            * 브라우저 기준의 성능 측정
                * ![image](https://user-images.githubusercontent.com/20143765/76754056-d7344780-67c4-11ea-9200-2cbf3f54e83c.png) 
                * DOMContentlLoaded 이벤트(파란색 표시), load 이벤트(빨간색 표시) 발생 시점이 빠를수록, 그리고 두 이벤트 발생 구간의 폭이 좁을수록 성능이 좋다고 말한다.
                * 크롬개발자 도구 DOMContentLoaded 이벤트(파란색 화살표), load 이벤트(빨간색 화살표) 발생 시점이 출력
                    * ![image](https://user-images.githubusercontent.com/20143765/76754071-db606500-67c4-11ea-84b3-b1ea9e5986cf.png)
                    * SPA에서는 웹 페이지에 포함된 적은 양의 HTML로 DOMContentLoaded, load 이벤트가 일찍 발생할 수 있으나, 이벤트가 발생한 이후에도 수많은 스크립트 실행으로 인해 여전히 "느린 로딩"이 존재
            * 사용자 기준의 성능 측정
                * FP, FCP, FMP, TTI 
                    * ![image](https://user-images.githubusercontent.com/20143765/76754079-de5b5580-67c4-11ea-8f3f-bca00f929266.png)
                * 중요한 시점은 FMP
                    * 흰 화면 대신 의미 있는 먼저 보여주어 사용자에게 긍정적인 인상을 줄 수 있다. 사용자 기준에서 성능을 좋게 하기 위해서 FMP를 앞당겨야 하고, 위에서 설명한 주요 렌더링 경로를 최적화하여 해결할 수 있다.
        * 성능 측정 도구
            * Performance 탭
            * 네트워크 탭
                * 리소스의 서버 요청 대기 시간 보기
                    * (1) Queuing : 대기열에 쌓아두는 시간
                        * 자바스크립트, CSS보다 우선순위가 낮아서 대기한다.
                        * TCP 소켓 대기
                        * TCP 연결 초과 대기
                        * 디스크 캐시 항목 작성 소요 시간
                    * (2) Stalled : 요청을 보내기 전의 대기 시간
                        * Queuing에서 쌓인 대기 시간 소모
                        * 프락시 협상에 드는 시간
                    * (3) DNS Lookup : DNS 조회에 소비된 시간
                    * (4) Initial connection : TCP 핸드셰이크/재시도 및 SSL을 포함한 연결을 설정하는 데 걸린 시간
                    * (5) Waiting(TTFB) : 초기 응답(Time To First Byte)을 기다리는 데 소비한 시간 (서버 왕복 시간)
                    * (6) Content Download : 리소스 실제 다운로드 시간
                    * ![image](https://user-images.githubusercontent.com/20143765/76754100-e3b8a000-67c4-11ea-9faf-0df62faeb231.png)
            * Audit 패널
                * 성능 측정 후 화면
                    * (1) Metrics : 다양한 성능 측정 지표를 보여주는 영역
                        * FCP, FMP, TTI 시점을 확인할 수 있다.
                        * 웹 페이지가 화면에 그려지는 단계를 스크린샷으로 보여준다.
                    * (2) Opportunities : 최적화 가능한 리소스 목록을 보여주는 영역
                    * (3) Diagnostics : 리소스 최적화 외에 성능을 개선할 수 있는 부분을 진단하고 해결 방안을 목록으로 보여주는 영역
                        * 주요 렌더링 경로를 최적화할 때 "Critical Request Chains" 영역을 참조한다.
                    * (4) Passed audits : 성능 측정 기준과 통과 목록을 보여주는 영역
                    * ![image](https://user-images.githubusercontent.com/20143765/76754108-e7e4bd80-67c4-11ea-8062-921c40776eb7.png)
    * 웹 페이지 로딩 최적화
        * 블록 리소스(CSS, 자바스크립트) 최적화
            * CSS 최적화
                * 렌더 트리를 구성하기 위해서는 DOM 트리와 CSSOM 트리가 필요하다. DOM 트리는 파싱 중에 태그를 발견할 때마다 순차적으로 구성할 수 있지만, CSSOM 트리는 CSS를 모두 해석해야 구성할 수 있다. 즉, CSSOM 트리가 구성되지 않으면 렌더 트리를 만들지 못하고 렌더링이 차단된다.
                * <head> 아래 배치
                * 특정 조건에서만 필요한 CSS가 있을 때 미디어 쿼리를 사용하면 불필요한 블로킹을 방지
                * @Import사용을 피한다, @import를 사용했을 때 브라우저는 스타일시트를 병렬로 다운로드 할 수 없기 때문에 로드 시간이 늘어날 수 있다.
            * 자바스크립트 최적화
                * 자바스크립트는 DOM 트리와 CSSOM 트리를 동적으로 변경할 수 있기 때문에 HTML 파싱을 차단하는 블록 리소스이다. <script> 태그를 만나면 스크립트가 실행되며 그 이전까지 생성된 DOM에만 접근할 수 있다. 그리고 스크립트 실행이 완료될 때까지 DOM 트리 생성이 중단된다. 외부에서 가져오는 자바스크립트의 경우에는 모든 스크립트가 다운로드되고 실행될 때까지 DOM 트리 생성이 중단된다. 이러한 이유로 자바스크립트도 렌더링 차단 리소스
                * <script> 태그에 defer나 async 속성을 명시하면 스크립트가 DOM 트리와 CSSOM 트리를 변경하지 않겠다는 의미이기 때문에 브라우저가 HTML 파싱을 멈추지 않는다.
            * Parse HTML을 줄여라
        * 리소스 요청 수 줄이기
            * 이미지 스프라이트
            * CSS, 자바스크립트 번들하기
            * 내부 스타일시트 사용하기
            * 작은 이미지를 HTML, CSS로 대체
                * Data URI
        * 리소스 용량 줄이기
            * 중복 코드 제거하기
            * 만능 유틸 사용 주의하기
            * HTML 마크업 최적화
                * 불필요한 태그, 공백, 주석 사용 (최적화 전)
            * 간결한 CSS 선택자 사용
            * 압축(Minify)하여 사용하기
