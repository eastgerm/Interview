# Javascript

### 1. == 와 === 의 차이점

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
