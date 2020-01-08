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
            
### 3. 함수 선언 방식의 차이점

- 개요
    - 자바스크립트에는 여러가지의 함수 선언 방식이 존재한다.
    - 각 선언 방식에는 어떠한 차이점이 있는지를 알고 써야한다고 생각했다.
    - 지금부터 어떠한 방식이 존재하고, 어떠한 차이점이 있는지 알아보겠다.
    
- 함수 선언 방식
    - 함수 선언문
        ```javascript
        function add(x, y) {    
          return x + y;
        }
        ```
        - 함수의 이름이 반드시 정의되어야 한다.
      
    - 함수 표현식
        ```javascript
        const add = function(x, y) {    
          return x + y;
        };
        ```
        - 자바스크립트에서는 함수도 하나의 값(객체)일 뿐이다.
        - 함수를 일급 객체라고 부른다. (추후 자세히 다룰 예정)
        - 여기서 사용된 'add'는 함수 이름이 아니라 함수를 참조하는 변수다.
        - function 키워드 뒤에 함수의 이름을 정의해도 상관없으나 어차피 사용되는 변수는 참조변수인 'add'이므로 불필요하다.
        - 익명함수를 만들고 'add'라는 이름으로 참조하겠다 라는 표현법이다.
        - 기명함수로 작성할 시 외부에서 함수 이름으로의 접근이 불가능하다.
        - 내부에서 재귀 호출을 하거나 디버깅의 용도가 아니라면 익명함수를 사용하는 것이 일반적이다.
        - 맨 뒷부분에 ;을 붙이는 것을 권장한다. (함수 정의가 끝났다고 ;으로 확실하게 밝혀야 파서에서 일어날 수도 있는 에러를 미연에 방지)
        ```javascript
        const factorialVar = function factorial(n) {    
          if (n <= 1) return 1;
          return n * factorial(n - 1);
        };
        ```
    
    - Function() 생성자
        ```javascript
        const add = new Function('x', 'y', 'return x + y');
        ```
        - 자바스크립트에 내장된 Function이라는 객체가 있다.
        - 이렇게 사용할 수도 있으나 거의 사용하지 않는다.
             
    - 화살표 함수
        ```javascript
        const add = (x, y) => {  
          return x + y;
        } 
        ```
        - es6에 등장한 방법으로 깔끔한 콜백함수 작성이 가능하다.
        - this가 function이 아니라 상위 객체를 가르키고 있기 때문에 좋을수도, 안좋을수도 있다. (개인적으로 매우 유용하게 사용 중이다.)

- 함수 호이스팅 (추후 자세히 다룰 예)
    - 함수 호이스팅이란 코드 에 있는 선언들을 모두 끌어올려서 해당 함수 유효 범위의 최상단에 선언하는 것을 말한다.
    - 함수 선언문으로 작성 시 호이스팅이 이뤄지기 때문에 선언 순서에 구애받지 않고 호출이 가능하다.
        ```javascript
        console.log(add(2, 3)); // 5
        function add(x, y) {    
          return x + y;
        }
        console.log(add(3, 4)); // 7
        ```
    - 함수 표현법으로 작성 시 호이스팅이 이뤄지지 않기 때문에 선언 순서가 중요해진다.
        ```javascript
        console.log(add(2, 3)); // uncaught type error !!
        const add = function(x, y) {    
          return x + y;
        };
        console.log(add(3, 4)); // 7
        ```정