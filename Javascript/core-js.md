### data type
- Primitive Type
  - Number
  - String
  - Boolean
  - null
  - undefined
  - Symbol
- Reference Type
  - Object
    - Array
    - Function
    - RegExp
    - Set / WeakSet
    - Map / WeakMap

### 실행 컨텍스트(execution context)
함수를 실행할 때 필요한 환경정를 담은 객체
- 전역공간
- `함수`
- ~~eval~~
- module
```javascript
var a = 1;
function inner() {
  console.log(a); // 1, 1 출력
  
  function outer() {
    console.log(a); // 2, undefined 출력
    var a = 3;
  }
  
  outer();
  console.log(a); // 3, 1 출력
}
inner();
console.log(a); // 4, 1 출력

// 전역 실행 컨텍스트 활성화
// inner 실행 컨텍스트 활성화
// outer 실행 컨텍스트 활성화
// outer 실행 컨텍스트 종료
// inner 실행 컨텍스트 종료
// 전역 실행 컨텍스트 종료
```
##### 콜스택(call stack)
- 현재 어떤 함수가 동작중인지, 다음에 어떤 함수가 호출될 예정인지 등을 제어하는 자료구조
- 스택 구조

##### 실행 컨텍스트 구조
- VariableEnvironment: 식별자 정보 수집, 변화 X
- `LexicalEnvironment`: 각 식별자의 데이터 추적, 변화 O
- ThisBinding

##### LexicalEnvironment
실행컨텍스트를 구성하는 환경 정보들을 모아 사전처럼 구성한 객체
- environmentRecord: 현재 문맥의 식별자 정보 수집(hoisting)
- outerEnvironmentReference: 현재 문맥에 관련 있는 외부 식별자 정보를 참조(scope chain)

##### hoisting
```javascript
console.log(a());
console.log(b());
console.log(c());

function a() {
    return 'a';
}
var b = function bb() {
    return 'bb';
}
var c = function() {
    return 'c';
}
```
```javascript
function a() {
  return 'a';
}
var b;
var c;

console.log(a());
console.log(b());
console.log(c());

b = function bb() {
    return 'bb';
}
c = function() {
    return 'c';
}
```
```text
environmentRecord: {
  function a() { ... },
  b: undefined,
  c: undefined
}
```

##### scope chain
변수를 가장 가까운 자기 자신부터, 점점 멀리있는 스코프 찾아 나가는 것(shadowing)

### this
- 전역공간에서: 전역객체, window(browser)/global(node.js)
- 함수 호출시: 전역객체
- 메서드 호출시: 메서드 호출 주체
- callback 호출시: 기본적으로는 함수내부에서와 동일
  - 명시적인 this 바인딩: call, apply, bind
    ```javascript

    ```
- 생성자함수 호출시
  - 
