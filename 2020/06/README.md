
## 2020.06.07
### 사내 엔지니어링 데이 Study
- 최신 FE기술을 활용한 React 컴포넌트 개발, best practice를 찾아나가는 여정. (with Apollo, Hooks)
- FE개발자의 모바일 블로그 SSR 적용기 - 어서와, SSR은 처음이지?
- React 인싸들이 사용하는 React Hooks -[x] 쇼핑웹 적용

## 2020.06.18
### hooks Study
- [리액트의 Hooks 완벽 정복하기](https://velog.io/@velopert/react-hooks#23-%EB%92%B7%EC%A0%95%EB%A6%AC-%ED%95%98%EA%B8%B0)
   * useEffect
       * 마운트 될 때만 실행하고 싶을 때(componentDidMount)

         * ``` javascript 
           useEffect(() => {
              console.log('마운트 될 때만 실행됩니다.');
           }, []);
           ```

       *  특정 값이 업데이트 될 때만 실행하고 싶을 때
           *   ``` javascript
               useEffect(() => {
                 console.log(name);
               }, [name]);

       * 뒷정리 하기
           * 컴포넌트가 언마운트되기 전이나, 업데이트 되기 직전에 어떠한 작업을 수행하고 싶다면 useEffect 에서 뒷정리(cleanup) 함수를 반환해주어야 합니다.
               * ``` javascript
                 useEffect(() => {
                   console.log('effect');
                   console.log(name);
                   return () => {
                     console.log('cleanup');
                     console.log(name);
                   };
                 });
                 ```
           * 오직 언마운트 될 때만 뒷정리 함수를 호출하고 싶으시다면 useEffect 함수의 두번째 파라미터에 비어있는 배열을 넣으면 디
   * useReducer
       * ``` javascript 
         import React, { useReducer } from 'react';

         function reducer(state, action) {
           // action.type 에 따라 다른 작업 수행
           switch (action.type) {
             case 'INCREMENT':
               return { value: state.value + 1 };
             case 'DECREMENT':
               return { value: state.value - 1 };
             default:
               // 아무것도 해당되지 않을 때 기존 상태 반환
               return state;
           }
         }

         const Counter = () => {
           const [state, dispatch] = useReducer(reducer, { value: 0 });

           return (
             <div>
               <p>
                 현재 카운터 값은 <b>{state.value}</b> 입니다.
               </p>
               <button onClick={() => dispatch({ type: 'INCREMENT' })}>+1</button>
               <button onClick={() => dispatch({ type: 'DECREMENT' })}>-1</button>
             </div>
           );
         };

         export default Counter;
         ```
       * Redux 에서는 액션 객체에는 어떤 액션인지 알려주는 type 필드가 꼭 있어야 하지만, useReducer 에서 사용하는 액션 객체는 꼭 type 를 지니고 있을 필요가 없습니다. 심지어, 객체가 아니라 문자열이나, 숫자여도 상관이 없습니다.
   * useMemo
       * 컴포넌트 내부에서 발생하는 연산을 최적화
       * ``` javascript 
         import React, { useState, useMemo } from 'react';

         const getAverage = numbers => {
           console.log('평균값 계산중..');
           if (numbers.length === 0) return 0;
           const sum = numbers.reduce((a, b) => a + b);
           return sum / numbers.length;
         };

         const Average = () => {
           const [list, setList] = useState([]);
           const [number, setNumber] = useState('');

           const onChange = e => {
             setNumber(e.target.value);
           };
           const onInsert = e => {
             const nextList = list.concat(parseInt(number));
             setList(nextList);
             setNumber('');
           };

           const avg = useMemo(() => getAverage(list), [list]);

           return (
             <div>
               <input value={number} onChange={onChange} />
               <button onClick={onInsert}>등록</button>
               <ul>
                 {list.map((value, index) => (
                   <li key={index}>{value}</li>
                 ))}
               </ul>
               <div>
                 <b>평균 값:</b> {avg}
               </div>
             </div>
           );
         };

         export default Average;
         ```
           * list 배열의 내용이 바뀔 때에만 getAverage 함수가 호출됩니다
   * useCallback
       * 함수가 매번 재생성 되는것을 최적화
       * useCallback 의 첫번째 파라미터에는 우리가 생성해주고 싶은 함수를 넣어주고, 두번째 파라미터에는 배열을 넣어주면 되는데 이 배열에는 어떤 값이 바뀌었을 때 함수를 새로 생성해주어야 하는지 명시
       * 아래는 같은코드
       * ``` javascript 
         useCallback(() => {
           console.log('hello world!');
         }, [])

         useMemo(() => {
           const fn = () => {
             console.log('hello world!');
           };
           return fn;
         }, [])
         ```
   * useRef
       * ``` javascript 
         import React, { useState, useMemo, useRef } from 'react';

         const getAverage = numbers => {
           console.log('평균값 계산중..');
           if (numbers.length === 0) return 0;
           const sum = numbers.reduce((a, b) => a + b);
           return sum / numbers.length;
         };

         const Average = () => {
           const [list, setList] = useState([]);
           const [number, setNumber] = useState('');
           const inputEl = useRef(null);

           const onChange = useCallback(e => {
             setNumber(e.target.value);
           }, []); // 컴포넌트가 처음 렌더링 될 때만 함수 생성
           const onInsert = useCallback(
             e => {
               const nextList = list.concat(parseInt(number));
               setList(nextList);
               setNumber('');
               inputEl.current.focus();
             },
             [number, list]
           ); // number 혹은 list 가 바뀌었을 때만 함수 생성


           const avg = useMemo(() => getAverage(list), [list]);

           return (
             <div>
               <input value={number} onChange={onChange} ref={inputEl} />
               <button onClick={onInsert}>등록</button>
               <ul>
                 {list.map((value, index) => (
                   <li key={index}>{value}</li>
                 ))}
               </ul>
               <div>
                 <b>평균 값:</b> {avg}
               </div>
             </div>
           );
         };

         export default Average;
         ```
   * customHooks
       * useInputs
       * usePromises
       * https://nikgraf.github.io/react-hooks/
       * https://github.com/rehooks/awesome-react-hooks
- [Introducing React Hooks](https://john015.github.io/introducing-react-hooks)
- [[ReactHook] 리액트 내장훅 사용하기 (useContext, useRef, useMemo, useCallback, useReducer, ...)](https://velog.io/@kwonh/ReactHook-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EB%82%B4%EC%9E%A5%ED%9B%85-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-useContext-useRef-useMemo-useCallback-useReducer-)
   - useReducer + useContext
      - ![image](https://user-images.githubusercontent.com/20143765/84997616-c7dce580-b189-11ea-8d39-480644aad248.png)
   - useImperativeHandle
   - useLayoutEffect
      - useEffect는 비동기식으로 동작해 성능상으로 이점이 있습니다. 하지만 비동기식으로 동작하기 때문에 브라우저가 화면을 그리는중에도 동작할 수 있어, 화면의 불일치나 화면이 깨지는등의 문제가 발생한다면 useLayoutEffect훅의 사용을 고려해야합니다. 일반적으로 useEffect를 우선 사용하되, 문제 발생시에 useLayoutEffect를 고려하면 됩니다.
   - useDebugValue 
      - 커스텀 훅 디버
   
