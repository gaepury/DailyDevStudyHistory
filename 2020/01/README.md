## 2020.01.04
* [[Outsider`s blog] 2019년 회고](https://blog.outsider.ne.kr/1472?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+rss_outsider_dev+%28Outsider%27s+Dev+Story%29)
* [Spring BootJunit5 테스트 (백기선님 인프런 강의)](https://wedul.site/647)
    * Junit5 추가된 기능
        * Test 이름 지정(@DisplayName)
        * Assert 방법
            * ![image](https://user-images.githubusercontent.com/20143765/71762667-7ca18400-2f15-11ea-94ec-b4fa34c648db.png)
        * 특정 조건이 맞는 경우만 테스트 진행(assumingThat)
        * 특정 동작하는 테스트들만 그룹화하여 테스트 하기(@Tag)
        * 커스텀 태그 만들기
            * ![image](https://user-images.githubusercontent.com/20143765/71762670-80cda180-2f15-11ea-9c5d-52dc08953187.png)
        * 반복 테스트하기(@RepeatedTest)
        * Parameter를 받아서 테스트 하기(@ParameterizedTest)
        * Parameter 조작하여 테스트 하기
        * 테스트 인스턴스
            * 테스트 간의 의존관계가 있기 때문에 클래스에 있는 모든 테스트들은 서로 다른 객체에서 실행 => 테스트에서 클래스 내부에 있는 인스턴스를 접근해서 값을 변경해도 다른 테스트에서 해당 데이터를 접근하면 기존 값으로 되있음
        * 테스트 순서(@Order)
        * 테스트 전역 properties
        * Junit5 확장팩
* [[Outsider`s blog] 기술 뉴스 #141 : 20-01-02](https://blog.outsider.ne.kr/1473?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+rss_outsider_dev+%28Outsider%27s+Dev+Story%29)
* [2019년 WebRTC 개발 이야기](https://blog.remotemonster.com/2019%EB%85%84-webrtc-%EA%B0%9C%EB%B0%9C-%EC%9D%B4%EC%95%BC%EA%B8%B0-635b452f37ac)
    * WebRTC(Web Real-Time Communication) 맨날 까먹네.
* [운영체제 - 디스크 관리](https://velog.io/@pa324/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%EA%B4%80%EB%A6%AC-xrk3texchp)
* [JavaScript ‪Module Cheatsheet](https://medium.com/dailyjs/javascript-module-cheatsheet-7bd474f1d829)
* [빽 투더 기본기 [OS 6편]. 메모리 관리 1](https://dailyheumsi.tistory.com/137?category=855210)
    * 페이지 테이블은 메인 메모리에 상주, 논리주소는 메모리 내 페이지 테이블을 거쳐, 원래 목적 메모리 주소에 도달하게 되는, 즉 2번 메모리를 접근하여 명령어를 수행
* [빽 투더 기본기 [OS 7편]. 메모리 관리 2](https://dailyheumsi.tistory.com/138?category=855210)
    * 메모리에 있는 페이지 테이블과 다르게, 캐시 메모리(하드웨어)에 별도로 (페이지 넘버 - 프레임 넘버)에 대한 매핑 정보를 담고 있는 테이블
    * 페이징 테이블 접근에 의한 메모리 2번 접근 이슈 개선
* [빽 투더 기본기 [OS 8편]. 가상 메모리 관리](https://dailyheumsi.tistory.com/139?category=855210)
* [http-decision-diagram](https://github.com/for-GET/http-decision-diagram/blob/master/doc/README_request.md#allowed_methods-var)
    * HTTP의 상태 코드를 결정하는 다이어그램. 200대부터 500대 코드까지 HTTP 요청 상황의 true/false로 따라가서 적절한 상태 코드를 찾을 수 있다
    * 꽤 유용할듯

--- 

## 2020.01.09
* [gRPC Reference - 예제](https://hyungyu-lee.github.io/articles/2020-01/grpc-2)
    * Proto file 작성
        * ![image](https://user-images.githubusercontent.com/20143765/72040425-d88c5400-32eb-11ea-9d93-5cf7494ea961.png)
            * proto 파일을 별도로 컴파일할 경우 mvn protobuf:{goal} 명령어로 컴파일 할 수 있다.
            * 컴파일된 결과물은 target(혹은 지정 빌드 디렉토리)/generated-sources/protobuf/java 이하 디렉토리에 생성된다.
            * message 는 서버-클라이언트 간 송수신될 데이터 포맷
            * service 는 서버, 클라이언트에서 원격 호출되는 서비스 메소드
    * 서버 프로그램 작성
        * 서비스 기능구현
            * ![image](https://user-images.githubusercontent.com/20143765/72040431-db874480-32eb-11ea-808b-a04591e941b5.png)
        * 작성한 서비스를 사용하는 서버 구현
            * ![image](https://user-images.githubusercontent.com/20143765/72040436-dfb36200-32eb-11ea-99d0-73c41de94653.png)
    * 클라이언트 프로그램 작성
        * ![image](https://user-images.githubusercontent.com/20143765/72040443-e4781600-32eb-11ea-9a9d-31c712534bad.png)

---

## 2020.01.17
 * [[자바스크립트] 엄격 모드(strict mode)](http://beomy.tistory.com/13)
    * 실수를 에러로 변환(Converting mistakes into errors)
       * 1. 선언하지 않고 전역 변수를 만들 수 없습니다.
       * 2. writable이 false로, 읽기 전용 객체에 쓰는 것이 불가능 합니다. (read only 객체 수정 불가능)
       * 3. get으로 선언된 객체는 수정할 수 없습니다. (getter-only property 수정 불가능)
       * 4. extensible 특성이 false로 설정된 객체에 속성을 확장 할 수 없습니다. (확장 불가 객체 확장 불가능)
       * 5. delete를 호출 할 수 없습니다.
       * 6. 리터럴 객체는 동일한 이름의 property를 가질 수 없습니다.(하지만ES6는 가능함)
       * 7. 함수의 동일한 매개 변수 이름을 선언하는 것이 불가능 합니다.
       * 8. 8진수 숫자 리터럴 및 이스케이프 문자를 사용 할 수 없습니다.
       * 9. primitive values의 속성 설정이 불가능합니다.
    * 변수 사용의 명료화(Simplify variable uses)
       * 10. with를 사용할 수 없습니다.
       * 11. eval 함수는 주변 스코프에 새로운 변수를 추가하지 않습니다.
    * eval과 arguments 명료화(Making eval and arguments simpler)
       * 12. eval을 변수 또는 함수, 매개 변수의 이름으로 사용할 수 없습니다.
       * 13. arguments를 변수 또는 함수, 매개 변수의 이름으로 사용할 수 없습니다.
       * 14. 인자값을 수정함으로 arguments의 값이 수정되지 않습니다.
       * 15. callee를 지원하지 않습니다.
    * 안전한 자바스크립트("Securing" JavaScript)
       * 16. this의 값이 null 또는 undefined인 경우 전역 객체로 변환하지 않습니다.
       * 17. callee, caller를 통해 stack 검색이 불가능합니다.
       * 18. arguments의 caller를 지원하지 않습니다.
    * 미래의 자바스트립트 준비(Paving the way for future ECMAScript versions)
       * 19. 예약된 키워드의 이름으로 변수 또한 함수를 생성할 수 없습니다
       * 20. 함수 선언은 스크립트나 함수의 최상위에서 해야 합니다.

## 2020.01.18
    * [7.10 Git 도구 - Git으로 버그 찾기](https://git-scm.com/book/ko/v2/Git-%EB%8F%84%EA%B5%AC-Git%EC%9C%BC%EB%A1%9C-%EB%B2%84%EA%B7%B8-%EC%B0%BE%EA%B8%B0)
    * [도커 컨테이너는 가상머신인가요? 프로세스인가요?](https://www.44bits.io/ko/post/is-docker-container-a-virtual-machine-or-a-process)
        * 도커 컨테이너의 프로세스 아이디는 1번
            * 리눅스 커널에 포함된 프로세스 격리 기술들을 사용
                * pid namespace
            * 셸의 pid 확인 : echo $$
        * PID 1번의 비밀, 도커 없이 일반 프로세스의 PID를 1번으로 실행하기
            * pid namespace 분리
                * 외에 UTS, PID, 네크워크, 마운트 등 다양한 종류의 namespace가 있음
            * unshare로 프로세스의 pid namespace 분리
        * 프로세스 ID를 격리하는 PID 네임스페이스
            * /proc 디렉터리: 프로세스 관련된 정보가 담겨져 있는 디렉토리
            * 1번 프로세스(init process) 아래 ns 디렉토리
                * ![image](https://user-images.githubusercontent.com/20143765/72868655-0464fc00-3d26-11ea-8879-0d55db92b341.png)
            *  기본적으로 모든 프로세스는 init 프로세스의 네임스페이스를 그대로 공유
                * ![image](https://user-images.githubusercontent.com/20143765/72868659-07f88300-3d26-11ea-8c2c-861a26d8dcf0.png)
