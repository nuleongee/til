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
var data = 1;
function func1() {
  console.log(data); // 1
  
  function func2() {
    console.log(data);
    var data = 3; // 2
  }
  
  func2();
  console.log(data); // 3
}
func1();
console.log(data); // 4

// 전역 실행 컨텍스트 오픈
// func1 실행 컨텍스트 오픈
// func2 실행 컨텍스트 오픈
// func2 실행 컨텍스트 종료 
// func1 실행 컨텍스트 종료 
// 전역 실행 컨텍스트 종료 
```
##### 콜스택(call stack)
- 현재 어떤 함수가 동작중인지, 다음에 어떤 함수가 호출될 예정인지 등을 제어하는 자료구조
- 스택 구조

##### 실행 컨텍스트 구조
- VariableEnvironment: 식별자 정보 수집, 변화 반영 X
- LexicalEnvironment: 각 식별자의 데이터 추적, 변화 반영 O
- ThisBinding
