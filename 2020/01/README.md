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
