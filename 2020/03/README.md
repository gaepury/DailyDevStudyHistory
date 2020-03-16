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
