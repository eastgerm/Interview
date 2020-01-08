# Javascript

### Object.create의 역할은 무엇인가요?
### 자바스크립트에서 모듈내의 private한 속성을 만드는 방법을 아는대로 쓰세요.
### JS에서 재귀호출로 인한 stack overflow를 막을 수 있는방법은?
### closure 와 스코프관계를 설명해보세요.
### == 보다, === 를 써야할때는?

- 개요
    - `==`은 **동등** 연산자 (a.k.a 느슨)
    - `===`은 **일치** 연산자 (a.k.a 철저)
    - 둘 다 이항 비교 연산자
    - 반환형은 true/false
    
- `==` 동등 연산자
    - loose equality
    - 양쪽 항을 강제 형변환
    - 그 이후 strict equal 인지를 판단 
    - 형변환을 거친 후!! strict한 비교를 하기에 전체적으로 보면 loose 한 것
    ```javascript
    0 == ''     //true
    0 == '0'     //true
    1 == true     //true
    false == '0'    //true
    null == undefined    //true
    false == null    //false
    false == undefined    //false
    ```
    - 너무 느슨한거 같다.
    - 진짜 모든게 같아야 같은거지 느슨하게 같다고 해버리면 추후에 큰 재앙이 다가 올 것만 같다.
    
- `===` 일치 연산자
    - strict equality
    - 양쪽 항을 있는 그대로 둔 채 strict equal 인지를 판단
    ```javascript
    0 === ''     //false
    0 === false    //false
    1 === true     //false
    NaN === NaN     //false
    null === undefined     //false
    ```
    - 철저하게 모든게 같아야 true값을 갖는다.
    
- 왜 `===`을 써야 하는가? Why?
    - 형변환한 결과가 어떤 사이에서 같은지 모두 알고 있기가 어려워 예측에 어려움이 있다.
    - Javascript는 애초에 type에 있어서 느슨한 언어이기 때문에 strict한 비교가 필수적이라고 생각한다.
    - 단순히 `==`비교만 한다면 true가 나올 경우들의 예측이 힘들어지니 `===`비교를 통해서 엄격한 체크가 이뤄져야 디버깅이 쉽고 개발자들의 마음이 편해진다. 
    
- Javascript에서 false의 의미를 지니는 것들
    - undefined, null
    - NaN
    - 0 (숫자 리터럴) , -0
    - “” (빈 문자열)
    - false

- 의외의 결과들
    - `""`은 false, but `[]`, `{}`는 true
        ```
        > Boolean("")
        false
        > Boolean([])
        true
        > Boolean({})
        true
        ```
    - NaN은 숫자가 아니라는 표현일 뿐 서로가 같다는 보장은 없다.
        ```
        > undefined === undefined
        true
        > null === null
        true
        > NaN === NaN
        false
        ```

### ES6의 Class extends 내부 동작원리에 대해서 설명해보세요.
### 객체를 탐색하는 방법에 대해서 2가지를 작성해보세요.
### NodeList 타입을, Array에 있는 reduce메서드를 사용하는 방법은?
### arrow 함수의 this가 결정되는 방식을 설명해보세요.
### undefined와 null의 차이점을 설명하세요.
### 아래처럼 동작하는 flatten함수를 reduce를 활용해서 만들어보세요.
```js
const arr = [[1, 2], [3, 4], [5, 6]];
const flattenedArray = flatten(arr);
console.log(flattenedArray)  //[1, 2, 3, 4, 5, 6];
``` 
### 객체를 복사해서 새로운 객체를 만들고 싶습니다. 코드를 구현해보세요. (객체의 깊이는 1단계만 있다고 가정)
### Array.from 이 모든 브라우저에서 동작하도록 polyfill코드를 만들어보세요.
### prototype 의 동작방식에 대해서 설명해보세요.
### 순환되는 캐로셀UI의 구현 원리에 대해서 설명해보세요.
### Event 객체에 대해서 설명해보세요.
### Array.from 이 모든 브라우저에서 동작하도록 polyfill코드를 만들어보세요.
### arrow 함수의 this가 결정되는 방식을 설명해보세요.
### 비동기의 장점을 설명해보세요.
### bind 가 필요한 상황을 간단한 코드로 보여주세요.
### CommonJS 스펙에 대해 설명해보세요.
### 클로저로 동작되는 상황을 예시코드로 보여주세요.
