## 2019.11.01(13개)
* [enable.auto.commit 일 때 Kafka consumer close() method 동작분석](https://blog.voidmainvoid.net/259)
    * 설명 미약..
* [[입 개발] Redis 버그 – Dataset 사이즈가 200GB가 넘어가면 죽는다구요?](https://charsyam.wordpress.com/2019/08/26/%EC%9E%85-%EA%B0%9C%EB%B0%9C-redis-%EB%B2%84%EA%B7%B8-dataset-%EC%82%AC%EC%9D%B4%EC%A6%88%EA%B0%80-200gb%EA%B0%80-%EB%84%98%EC%96%B4%EA%B0%80%EB%A9%B4-%EC%A3%BD%EB%8A%94%EB%8B%A4%EA%B5%AC%EC%9A%94/)
    * redis 내부 데이터 index 자료구조 int형 초과
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
    * redux form은 redux를 사용할때 편리한 장점이 있지만 성능상 이슈가 있다.
    
    
---

## 2019.11.02(22개)
* [Spring Batch 공통 설정 관리하기 (feat. 젠킨스 Environment variables)](https://jojoldu.tistory.com/445)
    * JAR_OPTS, JAR_NAME 공통 설정
       * ```
         java -jar ${JAR_OPTS} ${JAR_NAME} \
         --job.name=스프링배치Job이름 \
         파라미터1=파라미터값1 \
         파라미터2=파라미터값2
         ```

* Readlink(readlink란 심볼릭 링크가 연결되어 있는 원본의 파일명을 가져오는 명령어) 사용방식
   * ```
      java -jar ${JAR_OPTS} $(${JAR_NAME}) \
      --job.name=스프링배치Job이름 \
      파라미터1=파라미터값1 \
      파라미터2=파라미터값2
         ```
* [GraphQL is not just a network protocol](https://blog.cometkim.kr/posts/graphql-is-not-just-a-network-protocol/)
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
   * 드디어 GitHub actions setting 됨
   * github-actions-practice 연습용 repository 생성
* [[Spring & Design Pattern] Spring에서 발견한 디자인패턴_template method pattern](https://sabarada.tistory.com/19)    
   * Spring에서 사용되는 Template method pattern 
        * HttpServlet <-- FrameworkServlet <-- DispatcherServlet(doService method)
   * template method pattern 예제 코드
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
    
* [JSConf Korea에서 발표한 "Lessons from maintaining Mocha, an open source project” 발표자료](https://blog.outsider.ne.kr/1459?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+rss_outsider_dev+%28Outsider%27s+Dev+Story%29)
* [[번역] Refs와 DOM](https://velog.io/@pop8682/%EB%B2%88%EC%97%AD-Refs%EC%99%80-DOM)
* [Outsider 기술 뉴스 #137 : 19-11-01](https://blog.outsider.ne.kr/1464?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+rss_outsider_dev+%28Outsider%27s+Dev+Story%29)
* [클라우드알못에서 AWS 이직까지](https://reoim.tistory.com/entry/%ED%81%B4%EC%95%8C%EB%AA%BB%EC%97%90%EC%84%9C-AWS-%EC%9D%B4%EC%A7%81%EA%B9%8C%EC%A7%80)
   * 정말 멋진 이직기.. 어린 나이에 결혼 생활을 시작 하시면서 어떻게 저렇게 멋진 커리어를 꾸려 나갔으실지 그 노력들이 감히 가늠이 안된다.
* [스타트업 개발자가 리눅스 서버에 들어가면 언제나 하는 작업들](https://blog.outsider.ne.kr/1464?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+rss_outsider_dev+%28Outsider%27s+Dev+Story%29)
* [글로벌 서비스를 위한 멀티 리전 프록시 도입기](https://medium.com/benx-tech-blog/%EA%B8%80%EB%A1%9C%EB%B2%8C-%EC%84%9C%EB%B9%84%EC%8A%A4%EB%A5%BC-%EC%9C%84%ED%95%9C-%EB%A9%80%ED%8B%B0-%EB%A6%AC%EC%A0%84-%ED%94%84%EB%A1%9D%EC%8B%9C-%EB%8F%84%EC%9E%85%EA%B8%B0-87eda1bd8d55)
    * 해외 리전에 proxy ec2 인스턴스를 구축하여 nginx proxy(국내 ec2로) 처리
* [[번역] 오픈소스 에티켓](https://medium.com/jung-han/%EB%B2%88%EC%97%AD-%EC%98%A4%ED%94%88%EC%86%8C%EC%8A%A4-%EC%97%90%ED%8B%B0%EC%BC%93-bf59267d1db3)     
* [[Javascript] const와 Object.freeze()를 이용하여 Immutable한 Object 만들기](https://yorr.tistory.com/21)
* [16. 스프링부트 MVC - Transaction 속성 정리](https://linked2ev.github.io/gitlog/2019/10/03/springboot-mvc-16-%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8-MVC-Transaction-%EC%86%8D%EC%84%B1-%EC%A0%95%EB%A6%AC/)
    * 속성
        * propagation: 트랜잭션의 경계를 정의하며 시작 방법을 결정하는 속성, 각 속성은 document 참조
        * Isolation:  일관성이 없는 데이터를 허용하도록 하는 수준, 각 속성은 document 참조
        * readOnly: 트랜잭션이 시작된 이후 INSERT, UPDATE, DELETE 같은 쓰기 작업이 진행되면 예외가 발생한다.
        * timeout: 지정한 시간 내에 해당 메소드 수행이 완료되이 않은 경우 rollback 수행
        * rollbackFor:  롤백 룰을 정의해서 런타임 에러 발생 시에 롤백
* [Grafana와 엘라스틱서치 사용시 각종 query 조건 사용 방법(and, or, regex 등)](https://blog.voidmainvoid.net/270)
    1. exactly same document value 조건
       * ```topic.keyword: "discover_log-live”```
    2. OR 조건
       * ```topic.keyword: "discover_log-live" or topic.keyword: "test_log-dev”```
    3. AND 조건
       * ```topic.keyword: "discover_log-live" and partition_no.keyword: "2"```
    4. regex document value 조건
       * ```topic.keyword: /.*[live|alp]/```
     
---

## 2019.11.03(32개)
 * [[Spring & Design Pattern] Spring에서 발견한 디자인패턴_Proxy Pattern](https://sabarada.tistory.com/20)
     * @Transactional 어노테이션에 구현된 proxy pattern
 * [한글은 노토산스, 영문/숫자는 다른 폰트로 해주세요...](https://feel5ny.github.io/2019/09/08/CSS_02/)
     * ![image](https://user-images.githubusercontent.com/20143765/68080932-d5d33580-fe48-11e9-8b1e-712768a371a8.png)
     * uriencode-range로 폰트 자동 조절 가능
 * [Puppeteer로 크롤러 만들기 - 준비](https://yangeok.github.io/node.js/2019/09/09/puppeteer-crawler-pre.html)
 * [Puppeteer로 크롤러 만들기 - 페이지네이션](https://yangeok.github.io/node.js/2019/09/10/puppeteer-crawler-page.html)
 * [Puppeteer로 크롤러 만들기 - 무한스크롤](https://yangeok.github.io/node.js/2019/09/11/puppeteer-crawler-scroll.html)
 * REST 기반의 간단한 분산 트랜잭션 구현
     * [REST 기반의 간단한 분산 트랜잭션 구현 - 1편](https://www.popit.kr/rest-%EA%B8%B0%EB%B0%98%EC%9D%98-%EA%B0%84%EB%8B%A8%ED%95%9C-%EB%B6%84%EC%82%B0-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B5%AC%ED%98%84-1%ED%8E%B8/)
         *  TCC(Try-Confirm/Cancel) 방식
     * [REST 기반의 간단한 분산 트랜잭션 구현 - 2편 TCC Cancel, Timeout](https://www.popit.kr/rest-%EA%B8%B0%EB%B0%98%EC%9D%98-%EA%B0%84%EB%8B%A8%ED%95%9C-%EB%B6%84%EC%82%B0-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B5%AC%ED%98%84-2%ED%8E%B8-tcc-cancel-timeout/)
     * [REST 기반의 간단한 분산 트랜잭션 구현 - 3편 TCC Confirm(Eventual Consistency)](https://www.popit.kr/rest-%EA%B8%B0%EB%B0%98%EC%9D%98-%EA%B0%84%EB%8B%A8%ED%95%9C-%EB%B6%84%EC%82%B0-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B5%AC%ED%98%84-3%ED%8E%B8-tcc-confirmeventual-consistency/)
     * [REST 기반의 간단한 분산 트랜잭션 구현 - 4편 REST Retry](https://www.popit.kr/rest-%EA%B8%B0%EB%B0%98%EC%9D%98-%EA%B0%84%EB%8B%A8%ED%95%9C-%EB%B6%84%EC%82%B0-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B5%AC%ED%98%84-4%ED%8E%B8-rest-retry/)
* [[HTML] 좋은 사용자 경험(UX)을 제공하는 Form 만들기](https://armadillo-dev.github.io/html/ux/makes-good-ux-form-with-html/)
    * inputmode 속성 활용하기: 천 단위로 ,을 표기하고 싶을 때
    * 양식 자동 완성 기능 활용하기: autocomplete 속성 사용
    * 자동 대문자 활성화 방지(모바일): 'autocapitalize: off’ 속성 사용
* [[Kubernetes] 쿠버네티스 Deployment 란?](https://blog.wonizz.tk/2019/09/17/kubernetes-deployment/)
    * ![image](https://user-images.githubusercontent.com/20143765/68080933-da97e980-fe48-11e9-957a-4932cc30e4cb.png) 
* [504 Gateway Time-out 문제의 원인과 해결 방법](https://blog.lael.be/post/9251)
    * upstream이란 tomcat, node, php등 application을 가르킨다.
* [네트워크 모니터링이 궁금할땐 ? Packetbeat !](https://taetaetae.github.io/2019/09/08/network-monitor-by-packetbeat/)
    * elastic stack packetbeat 
* [우아한 스프링 배치 테크세미나 정리 및 후기 (by 우아한 형제들)](https://taetaetae.github.io/2019/09/29/woowabros-spring-batch/)
    > 1. 자기보다 경험이 “적은” 사람에게 “설득을 당할 수” 있어야 하고, 자기보다 경험이 “많은 사람을 설득” 시킬 수 있어야 한다.
    > 2. 무중단 배포에 대해 설명을 해주셨다. 이는 사실 스프링배치 나 Jenkins 와는 관련이 없지만 이 둘을 사용하면서 배포를 할때 리눅스의 명령어니 readlink와 ln -s를 활용하여 중단없이 배포를 할 수 있도록 한다고 한다. 필자는 이제까지 Jenkins의 끄기전 준비를 실행 하고 스케쥴러에 의해 다음 Job이 실행되지 않는것을 확인 후에 배포를 하곤 했었는데 이러한 기능을 통해 충분히 무중단 배포를 구성 해볼수도 있을껏 같았다.
    * 배치 어플리케이션을 구성하면서 가장 중요시 생각해야할 개념은 멱등성. 
        * 멱등성이란 연산을 여러번 적용 하더라도 결과가 달라지지 않는 성질을 의미
    * 관련해서 Keep Spring batch 복습
 * [운영체제 - 스케쥴링 알고리즘 기본](https://velog.io/@pa324/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C-%EC%8A%A4%EC%BC%80%EC%A5%B4%EB%A7%81-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B8%B0%EB%B3%B8-uwk12tlqwj)
    * FIFO, SJF(short job first), Priority-Based, Round Robin
* [python에서 비동기 프로그래밍 하기 (feat. Asyncio)](https://jay-ji.tistory.com/39)
    * asyncio
* 빽 투더 기본기 [OS]
    * [1편. 프로세스](https://dailyheumsi.tistory.com/129?category=855210)
        * Process creation
            * fork():  fork() 는 OS가 새로운 메모리 공간을 할당하도록 한 후, 현재 프로세스의 코드와 정보를 모두 새로운 메모리 공간에 복사하도록 한다.
            * exec(): exec() 는 OS가 현재 프로세스의 공간에 새로운 프로세스를 덮어쓰게 한다.
        * Zombie(좀비) vs Orphan(고아) Process
        * IPC
            * Share memory, messaging pass, pipe, message queue, socket, semiphore 등
    * [2편. 쓰레드](https://dailyheumsi.tistory.com/130?category=855210)
        * User-level Thread vs Kernel-level Thread
            * 유저 <-> 커널 모드 전환에서 오버헤드가 크다.
            * 커널 레벨 쓰레드 
                * 장점 : 안전성, 기능의 다양성
                * 단점 : 커널에서 기능을 제공하기 때문에 성능 저하
            *  유저레벨 쓰레드
                * 장점 : 전환 필요없기때문에 성능 좋음
                * 단점 : 프로세스 내에 쓰레드가 하나만 블로킹 되어도 나머지 쓰레드가 작동하기 어려움
        * 다중 스레드 모델
            * ![image](https://user-images.githubusercontent.com/20143765/68081217-caced400-fe4d-11e9-943a-ebe6651f894d.png)
        * [3편. CPU 스케줄링](https://dailyheumsi.tistory.com/131?category=855210)
            * 싱글레벨 큐(하나의 큐): FIFO, SJF(short job first), Priority-Based, Round Robin
            * 다중레벨 큐(여러개의 큐): 큐 간 독자적인 스케쥴링 알고리즘을 사용
        * [4편. 동기화와 Peterson’ 알고리즘](https://dailyheumsi.tistory.com/132?category=855210)
        * [5편. 뮤텍스와 세마포어](https://dailyheumsi.tistory.com/133?category=855210)
            * 뮤텍스는 임계 영역에 들어가는 쓰레드가 하나라면, 세마포어는 복수 개가 가능
            * > 세마포어는 뮤텍스가 될 수 있지만 (S = 1 인 경우), 뮤텍스는 세마포어가 될 수 없다.
            * 뮤텍스는 바이너리 값을 갖는 세마포어다.
* [운영체제 - 프로세스와 컨택스트 스위칭](https://velog.io/@pa324/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80-%EC%BB%A8%ED%83%9D%EC%8A%A4%ED%8A%B8-%EC%8A%A4%EC%9C%84%EC%B9%AD-8ik28uy8ud)
   * ![image](https://user-images.githubusercontent.com/20143765/68081356-108c9c00-fe50-11e9-95a6-b1bb1d837bf1.png)
   * 대부분의 IPC기법은 결국 커널 공간을 활용하는 것 이다.(커널 공간은 공유하기 때문, file방식 제외)
* [함수들에 대한 그래프 시각화](http://www.gisdeveloper.co.kr/?p=8285)
* [아파치 카프카 Lag 모니터링 대시보드 만들기](https://blog.voidmainvoid.net/279)
   * Burrow(link) : linkedin에서 공개한 opensource lag monitoring application입니다. rest api를 통해 lag 정보를 전달받을 수 있습니다.
   * Telegraf(link) : 데이터의 수집 및 전달에 특화된 agent입니다. 이 글에서는 configuration설정을 통해 burrow의 데이터를 ES에 넣는 역할을 한다.
* [pandas의 DataFrame에 대한 Inner Join, Outer Join, Left Join, Right Join](http://www.gisdeveloper.co.kr/?p=8255)
* [Scala CLASSES VS CASE CLASSES](https://sehajyang.github.io/2019/10/11/class-vs-case-class/)
* [아파치 카프카 테스트용 data generator 소개 - ksql-datagen](https://blog.voidmainvoid.net/269)
* [더이상 기다리지 않아도 되는 배치 무중단 배포](https://taetaetae.github.io/2019/10/13/batch-nondisruptive-deploy/)
    * readlink( 실제 링크를 얻어오는 명령어) 사용
    > Job이 실행중이라도 기존에 실행중인 Job은 기존 모듈을 바라보고 실행이 되고, 도중에 새로 배포가 되어도 기존 실행되는 Job에는 영향을 주지 않으며(심볼릭 링크에 연결되었던 과거 배포 경로에서 실행되고 있기 때문) 새롭게 배포된 후 Job이 실행될때도 배포된 경로의 > 심볼릭 링크의 > 실제 링크 즉, 새롭게 배포된 경로에서 실행되기 때문에 무중단 배포가 가능하게 된다.
* [Spring에서 Logback을 이용해서 필터없이 별도의 디렉토리에 로그를 남기는 방법 (Logback MDC 사용법, 동적 로그 남기기)](https://jeong-pro.tistory.com/199)
    * MDC: MDC는 Mapped Diagnostic Context다. 그냥 Logback에서 여러 메타 정보를 넣을 수 있고 공유되는 Map이라고 생각하면 쉽다.
* [2019 상반기 웹디자인 트렌드(상)](https://brunch.co.kr/@thinkaboutlove/273)
* [2019 상반기 웹디자인 트렌드(하)](https://brunch.co.kr/@thinkaboutlove/275)
* [자바스크립트 릿코드 #번외 카카오 코딩테스트 공채 문제 풀이 1](https://velog.io/@jakeseo_me/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EB%A6%BF%EC%BD%94%EB%93%9C-%EB%B2%88%EC%99%B8-%EC%B9%B4%EC%B9%B4%EC%98%A4-%EC%BD%94%EB%94%A9%ED%85%8C%EC%8A%A4%ED%8A%B8-%EA%B3%B5%EC%B1%84-%EB%AC%B8%EC%A0%9C-%ED%92%80%EC%9D%B4-v7k2iyddb2)
    * 숫자.toString(진법) 메소드는 숫자를 특정 진법의 숫자 문자열로 바꿔준다.


## 2019.11.08(2개)
* [스프링 책 읽기(Spring in action) - 3.고급 와이어링](https://bob-full.tistory.com/13)
* [스프링 책 읽기(Spring in action) - 4. 애스펙트 지향 스프링](https://bob-full.tistory.com/14)
   - 어드바이스
      - 애스펙트가 해야할 작업
      - before - 호출 전**, after 실행 후, after-running - 성공 후, after-throwing - 실패 후**, around - 전후로 간단한 기능
   - 조인 포인트
      - 어드바이스 적용 가능한 지점(point)
   - 포인트커트
      - 조인 포인트의 영역을 좁히는 일을 함
      - 어드바이스 = 무엇, 언제 // 포인트 커트 = 어디서
      - 간단하게, 클래스 메소드명 지정부터, 정규표현식 정의 도 가능
   - 애스펙트
      - 어드바이스 + 포인트커트 = 언제 무엇을 어디서 할지 정의한 것
   - 위빙
      - 타깃 객체에, 애스펙트를 적용하여 새로운 프록시 객체를 생성하는 절차
      - 컴파일 시간, 클래스로드 시간, 실행 시간에 위빙됨
   - 포인트 커트 작성
      - @Aspect, @PointCut, @Around
      
## 2019.11.09(3개)
* [CSRF is (really) dead](https://scotthelme.co.uk/csrf-is-really-dead/)
    * ```Set-Cookie: __Host-session=123; path=/; Secure; HttpOnly; SameSite=Lax```
* [2019년과 이후 JavaScript의 동향 – 브라우저 밖의 JavaScript 1](https://d2.naver.com/helloworld/7700312)
* [2019년과 이후 JavaScript의 동향 – 브라우저 밖의 JavaScript 2](https://d2.naver.com/helloworld/7975004)

## 2019.11.12(3개)
* [도커 볼륨](https://bcho.tistory.com/1360)
* [HTTP/3? 그게 뭔데?](https://velog.io/@devjeon1358/-HTTP3-%EA%B7%B8%EA%B2%8C-%EB%AD%94%EB%8D%B0-fwk2swcx8s)
    * HTTP/1, HTTP/2 에서 사용되던 TCP 연결 방식을 UDP 기반의 프로토콜(QUIC)로 변경, QUIC 기술을 사용하여 기존 TCP에서 사용되던 연결 수립 과정을 빠르게 처리
        * QUIC(Quick UDP Internet Connection): 구글에서 TCP가 가지는 응답속도의 문제의 해결을 중점으로 두고 개발한 UDP 프로토콜
    * HTTP/3을 사용할 수 있게 할려면 Web 서버도 QUIC을 지원할 수 있도록 다시 빌드해야 하는 High Cost, QUIC을 사용하기 위한 별도 브라우저 설정등으로 도입 판단하긴 아직 이른듯.
* [REST API 응답은 어떻게 줘야할까? (표준 Response 객체를 만들 수 있을까?, 정확하게 응답 처리를 하는 방법, 성공과 실패 응답)](https://jeong-pro.tistory.com/200)

## 2019.11.15(2개)
 * [Jackson 직렬화 옵션의 적절한 활용과 Jackson에 기여하기까지 (feat. 글로벌 캐싱)](https://hyperconnect.github.io/2019/10/28/jackson-serialize-for-global-caching.html?fbclid=IwAR3Dv2yptUM-RoOesRVqZ_o2XZ70mXHZJ9nyOpO4dwaWVvM4bp_rYv-Lddg)
 * [JDK Dynamic Proxy vs CGLib Proxy](https://dreamchaser3.tistory.com/9?category=710874)
     * JDK Dynamic Proxy
         * interface를 구현하는 class들만 target이 될 수 있다.
         * Java reflection을 사용해 target class의 method를 invoke하며, Advise대상이든 아니든 모든 method call마다 reflection invoke를 실시하므로 성능이 떨어진다.
     * CGLib Proxy
         * interface가 없어도 사용 가능
         * bytecode 사용해 target class의 method 호출
         * 'final' class or method에는 쓸 수 없음
     * Spring AOP의 ProxyFactoryBean의 두 proxy 사용
         * ProxyFactoryBean은 interface의 유무로 proxy를 자동으로 설정한다. interface를 하나 이상 구현하고 있는 class라면 JDK Dynamic Proxy를 생성한다. 반대로 interface를 전혀 구현하고 있지 않는 class라면 CGLib proxy를 생성한다. 
             > 결국 사용되는 case는 interface를 구현하고 있지만, CGLib proxy를 사용하고 싶을 때뿐일 것이다. ProxyTargetClass property를 true로 설정하면, CGLib proxy를 쓰겠다는 것이다. 반대로 false로 설정하면 쓰지 않겠다는 것이다. 
             > (주의) false로 설정했다 할지라도, target class가 interface를 구현하고 있지 않은 경우에는 CGLib proxy를 쓴다.
          * ```<aop:config proxy-target-class="true”>```

## 2019.11.16(6개)
 * [[git] github actions를 활용한 pipit 배포 자동화](https://blog.naver.com/pjt3591oo/221708923091)
 * [Nodejs 성능 최적화](https://velog.io/@pa324/Nodejs-%EC%84%B1%EB%8A%A5-%EC%B5%9C%EC%A0%81%ED%99%94-u1k2zkwoqq)
   - json serializable **fast-json-stringify** 라이브러리 사용
   - 비동기 처리 Promise.all 사용
 * [AWS 솔루션 아키텍트 어소시에이트 자격증 취득](https://blog.outsider.ne.kr/1465?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+rss_outsider_dev+%28Outsider%27s+Dev+Story%29)
 * [자바스크립트 디자인패턴 - 데코레이터 (Decorator)](https://velog.io/@pa324/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EB%94%94%EC%9E%90%EC%9D%B8%ED%8C%A8%ED%84%B4-%EB%8D%B0%EC%BD%94%EB%A0%88%EC%9D%B4%ED%84%B0-Decorator-ivk2zg2pf0)
 * [[Github Actions] Github 에서 Workflow 사용하기](https://velog.io/@devjeon1358/Github-Actions-Github-%EC%97%90%EC%84%9C-Workflow-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-8wk2y2ijbu)
 * [GitHub Action을 사용해 새로 올라온 전월세 방 목록 받아보기](https://ahnheejong.name/articles/receive-new-room-notification-mails-using-github-action/?fbclid=IwAR04PvyDxJA0VJyCCiDdsotVm8Iye43Zp5brGKh9mkPX0sCE1ryC460j6Qg)
 
 ## 2019.11.22(6개)
* [Github - Suggestion 기능 활용하기](https://nesoy.github.io/articles/2019-11/Github-suggestion)
* Quartz 스케줄러 적용 아키텍처 개선
  * [1편 모듈 분리](http://homoefficio.github.io/2019/09/28/Quartz-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%9F%AC-%EC%A0%81%EC%9A%A9-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-%EA%B0%9C%EC%84%A0-1/)
     * 키워드: 모듈 분리와 URLClassLoader
     * ![image](https://user-images.githubusercontent.com/20143765/69397788-e5002180-0d2a-11ea-969b-ad329dec1190.png)
  * [2편 의존 관계 주입](http://homoefficio.github.io/2019/09/29/Quartz-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%9F%AC-%EC%A0%81%EC%9A%A9-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-%EA%B0%9C%EC%84%A0-3/)
     * 키워드: 의존 관계 주입과 SpringBeanJobFactory
     * ![image](https://user-images.githubusercontent.com/20143765/69397790-e893a880-0d2a-11ea-8c87-f94bb0598068.png)
  * [3편 트랜잭션 처리](http://homoefficio.github.io/2019/09/29/Quartz-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%9F%AC-%EC%A0%81%EC%9A%A9-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-%EA%B0%9C%EC%84%A0-3/)
     * 키워드: 트랜잭션 처리와 PlatformTransactionManager
     * ![image](https://user-images.githubusercontent.com/20143765/69397793-eb8e9900-0d2a-11ea-9390-9152557d5547.png)
* [<번역>앱의 프론트엔드 성능을 향상시키는 방법 - 5가지 코딩 팁](https://junwoo45.github.io/2019-10-05-frontend-performance/)
* [아틀라시안 취업후기](https://tacogrammer.com/%EC%95%84%ED%8B%80%EB%9D%BC%EC%8B%9C%EC%95%88-%EC%B7%A8%EC%97%85%ED%9B%84%EA%B8%B0/)
    * 면접질문
       * 프로젝트 구성, 사용하는 기술들에 관해 설명
       * 가장 선호하는 언어와 이유, 자바에 추가되면 좋을 것 같은 기능
       * 확장성 있는 서비스 어떻게 설계하나,
       * 데드락이 무엇이며 어떻게 방지하는가
       * 서버 느려 졌을 때 프로파일링 하는 방법
       * JVM 메모리 관련 튜닝 경험들, JVM 메모리 구조에 대해서 설명해보라
       * 시큐어 코딩하는 방법. XSS등 웹 보안 취약점 설명하고 어떻게 막을 수 있는지
* [Outsider 기술 뉴스 #138 : 19-11-16](https://blog.outsider.ne.kr/1466?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+rss_outsider_dev+%28Outsider%27s+Dev+Story%29)

## 2019.11.23(2개)
* [Reactive Streams (1)](https://jongmin92.github.io/2019/11/07/Java/reactive-2/)
* [Reactive Streams (2)](https://jongmin92.github.io/2019/11/07/Java/reactive-2/)

## 2019.11.28(1개)
* [[JUnit] JUnit5 사용법 - Parameterized Tests](https://gmlwjd9405.github.io/2019/11/27/junit5-guide-parameterized-test.html)
     * 사용하기
         * gradle
             * ![image](https://user-images.githubusercontent.com/20143765/69771595-b8d41d00-11d0-11ea-81f8-6b2e93868ad8.png)
     * Parameterized Tests
         * @ParameterizedTest 이 annotation을 추가하는 것을 제외하고는 다른 테스트와 동일하다.
         * ![image](https://user-images.githubusercontent.com/20143765/69771604-c4274880-11d0-11ea-9781-17fd1273f977.png)
     * Simple Value
         * @ValueSource
             * 해당 annotation 에 지정한 배열을 파라미터 값으로 순서대로 넘겨준다.
             * test method 실행 당 하나의 인수(argument) 만을 전달할 때 사용할 수 있다.
             * c.f. literal values 종류: short, byte, int, long, float, double, char, java.lang.String, java.lang.Class
             * ![image](https://user-images.githubusercontent.com/20143765/69771619-cdb0b080-11d0-11ea-96bc-bb1831a767dc.png)
     * Null And Empty Values
         * @NullSource
         * @EmptySource
         * @NullAndEmptySource
     * Enum
         * @EnumSource
         * ![image](https://user-images.githubusercontent.com/20143765/69771632-dacd9f80-11d0-11ea-8eea-c905f64988f0.png)
     * Method
         * @MethodSource
             * @MethodSource는 test method 실행 당 복잡한 인수 를 전달할 때 사용하는 방법
             * ``` java
               @ParameterizedTest
               @MethodSource("provideStringsForIsBlank") // needs to match an existing method.
               void isBlank_ShouldReturnTrueForNullOrBlankStrings(String input, boolean expected) {
                   assertEquals(expected, Strings.isBlank(input));
               }
               ```
             * ``` java
                // a static method that returns a Stream of Arguments
                private static Stream<Arguments> provideStringsForIsBlank() { // argument source method
                    return Stream.of(
                      Arguments.of(null, true),
                      Arguments.of("", true),
                      Arguments.of("  ", true),
                      Arguments.of("not blank", false)
                    );
                }
               ```
             * ``` java
                @ParameterizedTest
                @MethodSource("com.baeldung.parameterized.StringParams#blankStrings") // 클래스 외부의 source method
                void isBlank_ShouldReturnTrueForNullOrBlankStringsExternalSource(String input) {
                    assertTrue(Strings.isBlank(input));
                }
               ```
             * ``` java
                public class StringParams {
                  static Stream<String> blankStrings() {
                      return Stream.of(null, "", "  ");
                  }
                }
               ```

---

## 11월 블로그 총 본개수: 89개
