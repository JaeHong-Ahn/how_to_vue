# How To Vue

SSR : Server Side Rendering
- 서버에 페이지 요청
- 서버에서 페이지 전달

CSR: Client Side Rendering
- 서버로 초기화 요청
- 서버에서는 데이터만 보내줌 ( 초기화용 HTML 한번만 줌 )
    - 서버 부담이 줄음
    - 클라이언트는 페이지 전환이 빠름
- Vue.js

Vue를 사용하는 이유
- JS DOM을 사용하는 것은 매우 피곤한 작업임에도 쉽게 할 수 있음
- 동적 데이터 처리를 수월하게 수행 가능
- 컴포넌트 기반으로 UI 요소들을 모듈화 가능
- Vue에서 제공하는 디렉티브들도 조건문이나 반복문 등을 쉽게 구현 가능
- 가볍고 성능이 좋음
- 리액트보다 문법이 html 친화적이고 간결함

## 생명 주기 훅

각 Vue 컴포넌트 인스턴스는 생성될 때 일련의 초기화 단계를 거침
- 데이터 감시 설정
- 템플릿 컴파일
- 인스턴스를 DOM에 마운트
- 데이터가 변경되면 DOM을 업데이트
- 이 과정에서 생명주기 훅 함수도 실행되며 특정 단계에서 개발자가 의도하는 로직이 실행될 수도 있음

## 라이프 사이클 활용
### 1. created
컴포넌트 인스턴스가 생성된 직후 DOM이 아직 생성되지 않은 시점

### 2. mounted
컴포넌트에서 DOM이 만들어진 시점
주로 외부 데이터나 라이브러리를 추가하는 시점

### 3. updated
데이터가 변경되면 DOM을 업데이

### 4. unmounted ( destroyed )
컴포넌트가 종료될 때