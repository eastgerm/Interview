# React
### 1. 서버사이드 렌더링(SSR)은 무엇인가

- 개요
    - 검색엔진 최적화(SEO) 가능
    - SSR이 아니여도 구글엔진은 자바스크립트 엔진 내장이라 괜춘
    - 하지만 네이버나 다음 같은 곳에 검색이 되게 하려면 ssr 구현이 필수적임

- 장점
    - 초기 렌더링을 클라이언트가 아닌 서버에서 해주고
    - 그 결과만을 초기 html로 갖기에 로딩 속도에서 이점
    
- 단점
    - 성능 악화의 가능성
        - 서버사이드 렌더링을 하게 될 때는, ReactDOMServer.renderToString 함수를 사용하게 된다.
        - 이들은 동기적이기에 랜더링 동안은 이벤트루프가 막힘 (성능 악화 주요인)
    
### 2. React 키워드 모음집

- 개요
    - 리액트가 지닌 특징은 매우 많다.
    - 너무도 많기에 우선 키워드로만 한번 정리하고 나아가보려 한다.
    
- 키워드
    - React는 SPA
    - SPA이기에 초기 구동 속도가 느림
    - SEO 문제가 있을 수 있음
    - 서버사이드 렌더링을 지원
    - Virtual DOM을 사용
    - 단방향 데이터 흐름을 가짐
    - 자체 문법인 JSX 사용
    - 순수 컴포넌트란 동일한 상태에서 동일한 결과를 반환하는 것을 말함
    - state는 변경 가능성이 있는 정보를 담는 객체
    - props는 외부에서 들어온 정보를 담는 객체
    - state는 변수, props는 상수(매개변수)
    - state를 직접 업데이트하면 변화를 감지하지 못함
    - 상태의 변경은 무조건 setState를 이용
    - 이벤트 이름은 camelCase
    - 자체 추상화 이벤트인 synthetic event(합성 이벤트)
    - 인라인 조건식이 가능
    - key가 있기에 Virtual DOM에서 이득이 생기는 것
    - DOM 접근은 ref를 통해서 함
    - forwardRef는 child에게 전달하기 위함
    - Initialization, Mounting, Updation, Unmounting
    - Higher-Order components
    - props.children
    - constructor 안에서 만큼은 `super(props);`가 없으면 참조 못함
    - reconciliation