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

### 2. 자바스크립트 데이터 타입

- 개요
    - 자바스크립트는 type에 매우 관대한 언어다. (**느슨한 타입 체크 언어**)
    - C나 Java는 char, int, float, double 등의 예약어를 이용하여 변수의 데이터 타입을 지정해야 한다.
    - 반면 자바스크립트는 const, let 2가지 키워드 만으로 변수를 선언하기에 어떠한 타입의 데이터든지 저장이 가능하다.
    - var이라는 키워드도 있지만 요즘 사용하기엔 좀 부끄러운 면이 있다. (**es6 스펙을 애용하자**)
    - 느슨함에서 오는 주의사항이 생기므로 정리를 해보려 한다.
    
- 자바스크립트의 데이터 타입
    - 기본 타입
    - 참조 타입 (객체)
        - 자바스크립트에서 기본 타입을 제외한 모든 값은 객체다.
        - 배열도 함수도 객체다.
        - 단순히 `key:value` 형태로 프로퍼티들을 저장하는 컨테이너이다.
        - 객체는 참조값을 비교하므로 사용에 특히 유의 해야한다.
        
- 기본 타입
    - 숫자 (Number)
        - 정수, 실수의 구분이 없다.
        - C처럼 정수형 계산을 기대하지 마라 (ex. 5/2는 2가 아니다)
    - 문자열 (String)
        - char형이 없기에 한글자의 문자열도 string이다.
        - 한번 생성된 문자열은 읽기만 가능하고 수정은 불가능하다. (직접 해보면 안다. 좀 놀랐다.)
    - 불리언값 (Boolean)
        - true / false (명료하지만 개인적으론 가장 중요하다고 생각된다. ==과 ===을 확실하게 사용하기 위해서)
    - undefined
        - 아예 할당이 되지 않은 변수
        - '할당 되지 않았다'라는 뜻의 값이다.
    - null
        - 할당은 되었으나 값이 비어있음을 나타내는 변수
        - '빈값이 할당 되었다'라는 뜻의 이다.
        
- 참조 타입
    - 객체 (Object)
        - 배열 (Array)
        - 함수 (Function)
        - 정규표현식
            