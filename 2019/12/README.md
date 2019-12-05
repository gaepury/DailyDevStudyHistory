## 2019.12.02
* [React Hook 정리](https://velog.io/@noyo0123/React-Hook-%EC%A0%95%EB%A6%AC)
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
  - TestConfiguration
     - 기존에 정의했던 Configuration을 커스터마이징하고 싶은 경우 TestConfiguration 기능을 사용. TestConfiguration은 ComponentScan 과정에서 생성될 것이며 해당 자신이 속한 테스트가 실행될때 정의된 빈을 생성하여 등록할 것
     - 더 좋은 방법은 @Import 어노테이션을 사용하는 것. @Import 어노테이션을 통해서 직접 사용할 TestConfiguration을 명시
       - ![image](https://user-images.githubusercontent.com/20143765/70228639-03890280-1798-11ea-8d26-258167842c85.png)
  - MockBean and SpyBean
     - spring-boot-test 패키지는 Mockito를 포함
  - Properties
    - 별도의 테스트를 위한 application.properties(또는 application.yml)을 지정(vm옵션도 지정가능)
  - Web Environment test
  - TestRestTemplate
     - MovcMvc와 차이: Servlet Container를 사용하느냐 안하느냐의 차이. MockMvc는 Servlet Container를 생성하지 않는다.. 반면, @SpringBootTest와 TestRestTemplate은 Servlet Container를 사용한다.
  - 트랜젝션   
     - RANDOM_PORT나 DEFINED_PORT로 테스트를 설정하면 실제 테스트 서버는 별도의 스레드에서 수행되기 때문에 rollback이 이루어지지 않는다.
  - ApplicationContext 캐시
     -  동일한 ApplicationContext 사용
