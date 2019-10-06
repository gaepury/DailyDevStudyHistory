#### 2019.09.02
- 프로세스와 스레드

#### 2019.09.08
* 문서 엔지니어링과 API 문서화
* Protocol Buffers Language Guide (휘리릭 읽는 프로토콜 버퍼 문법 및 작성 시 유의 사항, 이것만 알면 .proto 파일을 이해할 수 있다?)
    * 와닿지 않늗다..
* Spring boot Resttemplate 사용시 HttpComponentsClientHttpRequestFactory 옵션 설명(setConnectTimeout, setConnectionRequestTimeout, setReadTimeout)
    * 여러 set options들
* (Troubleshooting) 레디스 사망일기
* JavaScript 배열(Array)의 발전과 성능에 대해서 자세히 알아보기
    * Javascript 배열
        * 같은타입의 배열을 사용해라(내부적으로 연속적인 메모리를 가진 배열로 변환). 그렇지 않으면 성능상으로 확연히 느려진다.
    * Typed Array
        * ArrayBuffers, Int8Array, Uint8Array, Uint8ClampedArray, Int16Array, Uint16Array, Int32Array, Uint32Array, Float32Array, Float64Array
* 지속 가능한 데이터 분석하기(지그재그)
    * 지그재그 회사 괜찮네..
* Kafka end Friends (ppt)
*  React + Storybook + puppeteer + jest 개발환경 구축하기
    * 코드, 에셋 변경에 대한 UI 영향도를 즉각적으로 확인
    * 실제 출력 결과를 비교하여 개발자에게 알려주므로 편리
* 파사드 패턴과 추상 팩토리 패턴
* CompletableFuture, parallelStream, ExecutorSev
* Docker 기반 분산 트랜스코더 개발
* [책 리뷰] 자바 최적화 (Optimizing Java,가장 빠른 성능을 구현하는 검증된 10가지 기법)
    * 사자
* Item 9. try-finally 보다 try-with-resources를 사용하라.
* Docker 기반 분산 트랜스코더 개발
* 자바 Enum 실무에 적용 경험 공유하기 (properties에서 enum mapping, default value 사용하기)
* AWS 자격증 시험 - 클라우드 종사자(Cloud Practitioner) 후기
    * 용호님 글
* Elasticsearch 특정 형태소 종류를 제외하여 검색하는 필터 nori_part_of_speech 적용
* Elasticsearch nori 형태소 분석기에서 readingform filter를 이용해서 한자 내용을 한글로 변환하기
* Apollo Client는 Redux와 무엇이 다른가
    * Redux 단점
        * REST API를 사용하기 때문에 리소스의 크기가 서버에서 결정된다. 데이터 교환이 복잡하게 이루어지고, 엔드포인트 증가 및 overfetching과 underfetching 등의 문제점
* [Node.js] Redis로 캐싱 시스템 구축하기
* 5. 신입 개발자 면접 질문 모음 (클라우드, 인프라)
* Spring에서 HMAC-SHA256 인증해보기
* 다시쓰는 Flask unittest (상,하편)
* 2019년과 이후 JavaScript의 동향 - JavaScript(ECMAScript)
* [번역] Elasticsearch 퍼포먼스 튜닝 방법 - ebay
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
* React, Typescript, Webpack환경에서 번들링 속도 올리기
* Python 로그를 남기는 Logbook 라이브러리 알아보기
* 고객 행동 기반 실시간 딥 뉴럴 추천 시스템 : ForYou
* 주니어 개발자가 반응형 레이아웃 리팩토링한 썰.txt
