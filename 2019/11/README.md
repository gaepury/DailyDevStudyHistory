## 2019.11.01
* [enable.auto.commit 일 때 Kafka consumer close() method 동작분석](https://blog.voidmainvoid.net/259)
    * 설명 미약..
* [[입 개발] Redis 버그 – Dataset 사이즈가 200GB가 넘어가면 죽는다구요?](https://charsyam.wordpress.com/2019/08/26/%EC%9E%85-%EA%B0%9C%EB%B0%9C-redis-%EB%B2%84%EA%B7%B8-dataset-%EC%82%AC%EC%9D%B4%EC%A6%88%EA%B0%80-200gb%EA%B0%80-%EB%84%98%EC%96%B4%EA%B0%80%EB%A9%B4-%EC%A3%BD%EB%8A%94%EB%8B%A4%EA%B5%AC%EC%9A%94/)
* [[Spring] mockMvc로 Controller 테스트 (ContentType)](https://blog.naver.com/writer0713/221629279019)
* [[Spring] MVC 단위테스트](https://blog.naver.com/writer0713/221630444346)
    * Controller -> Mock BO
    * BO -> Mock Repository
    * Repository -> Mock Data
* [반응형 웹 - 1. 뷰포트 (feat. React, styled-components)](https://eblee-repo.tistory.com/47)
* [반응형 웹 - 2. 그리드 뷰 (feat. React, styled-components)](https://eblee-repo.tistory.com/48)
* [반응형 웹 - 3. 미디어 쿼리 (feat. React, styled-components)](https://eblee-repo.tistory.com/49)
* [AWS Lambda, Docker로 테스트하기 (with Python)](https://yahwang.github.io/posts/77)
    * lambci/lambda:build-XXXX 형식으로 언어별로 image를 제공
 * [머신러닝의 앙상블[ensemble]이란? - 배깅(baggage), 부스팅(boosting), 보팅(voting) 학습](https://lsjsj92.tistory.com/515)
 * [Memchcahed 개념과 특징](https://goodgid.github.io/Memcached/)
 * [Docker Container 내부 소켓 상태 확인 - nsenter와 netstat](https://aidanbae.github.io/code/docker/docker-netstat/)
     * nsenter: namespace enter의 약자
     * ```sudo nsenter -t 15652 -n netstat```
 * [Accuracy, Precision, Recall](http://www.gisdeveloper.co.kr/?p=8146)
 * [라이브러리 추천: react-hook-form](https://velog.io/@iamchanii/react-hooks-form-%EC%9D%84-%EC%86%8C%EA%B0%9C%ED%95%A9%EB%8B%88%EB%8B%A4-54k0rrj6m7)
    * - redux form은 redux를 사용할때 편리한 장점이 있지만 성능상 이슈가 있다.
* [Spring Batch 공통 설정 관리하기 (feat. 젠킨스 Environment variables)](https://jojoldu.tistory.com/445)
    * JAR_OPTS, JAR_NAME 공통 설정
```
java -jar ${JAR_OPTS} ${JAR_NAME} \
--job.name=스프링배치Job이름 \
파라미터1=파라미터값1 \
파라미터2=파라미터값2
```

   * Readlink(readlink란 심볼릭 링크가 연결되어 있는 원본의 파일명을 가져오는 명령어) 사용방식
```
java -jar ${JAR_OPTS} $(${JAR_NAME}) \
--job.name=스프링배치Job이름 \
파라미터1=파라미터값1 \
파라미터2=파라미터값2
```
* [GraphQL is not just a network protocol}(https://blog.cometkim.kr/posts/graphql-is-not-just-a-network-protocol/)
    * 상태관리(Redux같은)로서 GraphQL를 활용한 흥미로운 예
    * GraphQL의 유즈케이스를 살펴보면 실제로 데이터베이스, 마이크로서비스, API 서버, 모바일 클라이언트 등 말 그대로 데이터를 다루는 모든 곳에서 활용되고 있다.
    * 저자는 DB들이 SQL 보다 GraphQL을 기본 쿼리 언어로 제공하게 되는 것이 앞으로의 트렌드라고 말하고 있음.
    * Relay
        > Relay는 React 애플리케이션을 위한 데이터 관리 프레임워크입니다. Relay의 중요한 특징은 각 컴포넌트마다 필요한 데이터를 선언하고, 컴포넌트의 계층 구조를 따라서 필요한 데이터를 상위 컴포넌트로 전달 및 조합하여 단일 GraphQL 쿼리로 만들어 준다는 것입니다. (그래서 이름이 Relay인 것이죠!)
* [Unit Test (단위 테스트) 에 관한 생각](https://gregor77.github.io/2019/08/16/about-unit-test/)
* [[번역] 최신 네트워크 로드 밸런싱 및 프록시 소개](https://ziwon.dev/post/modern-network-load-balancing-and-proxying/)
* [샤딩과 파티셔닝의 차이점](http://theeye.pe.kr/archives/1917)
    * **샤딩은 수평 파티셔닝과 동일**
* [Spring 테스트 코드 작성에 대한 나름의 고찰](https://www.popit.kr/spring-%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%BD%94%EB%93%9C-%EC%9E%91%EC%84%B1%EC%97%90-%EB%8C%80%ED%95%9C-%EB%82%98%EB%A6%84%EC%9D%98-%EA%B3%A0%EC%B0%B0/?fbclid=IwAR1ZHQKZ-jsQ1L9XxxJMnBdsSxGhLpZzF1WRw6fyZMiDOB_n3AkV_CyVYiQ)
* [Spring 기반 - ConstraintValidator을 이용해서 효과적인 검증](https://www.popit.kr/spring-%ea%b8%b0%eb%b0%98-constraintvalidator%ec%9d%84-%ec%9d%b4%ec%9a%a9%ed%95%b4%ec%84%9c-%ed%9a%a8%ea%b3%bc%ec%a0%81%ec%9d%b8-%ea%b2%80%ec%a6%9d/)
    * 날씨 신규 프로젝트에서 만든방식과 동일
    * 차이점
        * @RequestBody에 모델 객체 전체를 validation처리
        * @Valid사용
* [Spring Security 개념 잡기](https://junebuug.github.io/2019-09-05/spring-security)
* [Spring Security 인프런 강의 정리](https://lelecoder.com/140)
    * 직접 강의 봐야겠다..
 * [[git] gitHub actions 간단하게 알아보자](https://blog.naver.com/pjt3591oo/221639403758)
    * 드뎌 GitHub actions setting 됨
    * github-actions-pracie 연습용 repository 생성
* [[Spring & Design Pattern] Spring에서 발견한 디자인패턴_template method pattern](https://sabarada.tistory.com/19)    
 ``` java
// 1. Worker
package com.main;
public abstract class Worker {

    public void DailyRoutine()
    {
        getUp();
        eatBreakfast();
        goToWork();
        work();
        returnToHome();
        relax();
        sleep();
    }

    private void getUp()
    {
        System.out.println("getUp!");
    }

    private void eatBreakfast()
    {
        System.out.println("getBreakfast");
    }

    private void goToWork()
    {
        System.out.println("goToWork");
    }

    protected abstract void work();

    private void returnToHome()
    {
        System.out.println("returnToHome");
    }

    protected abstract void relax();

    private void sleep()
    {
        System.out.println("sleep");
    }
}
// 2. FireFighter

package com.main;

public class FireFighter extends Worker{

    @Override
    protected void work() {
        System.out.println("FireFighter`s work");
    }

    @Override
    protected void relax() {
        System.out.println("FireFighter`s relax");
    }
}
// 3. Postman

package com.main;

public class Postman extends Worker {

    @Override
    protected void work() {
        System.out.println("Postman`s Work");
    }

    @Override
    protected void relax() {
        System.out.println("Postman`s relax");
    }

}
// Main
package com.main;

public class Main {

    public static void main(String[] args) {

        Worker fireFighter = new FireFighter();
        Worker postMan = new Postman();

        fireFighter.DailyRoutine();
        System.out.println("--------------------------------");
        postMan.DailyRoutine();
    }
}
```
   * Spring에서 사용되는 Template method pattern 
      * HttpServlet <-- FrameworkServlet <-- DispatcherServlet(doService method)