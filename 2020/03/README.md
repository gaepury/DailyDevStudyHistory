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
