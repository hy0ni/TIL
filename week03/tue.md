2025-01-21

## localStorage란?

localStorage는 브라우저에서 제공하는 웹 스토리지 API 중 하나로, 데이터를 영구적으로 저장하기 위한 클라이언트 측 저장소다.

특징

- 브라우저를 닫거나 컴퓨터를 재시작해도 데이터가 유지된다.
- 키-값(key-value) 형태로 데이터를 저장한다.
- 최대 저장 용량은 일반적으로 약 5MB이다.
- 데이터는 문자열 형식으로 저장된다.

### localStorage를 사용하는 이유

(1) 브라우저 내 영구 데이터 저장

- 브라우저 내에서 간단한 데이터를 영구적으로 유지해야 할 때 사용한다.
  - 예: 사용자 설정, 인증 정보, 캐시된 데이터 등.

(2) 서버와의 통신 부담 감소

- 데이터를 LocalStorage에 저장하여 서버 요청을 줄이고 성능을 개선할 수 있다.
  - 예: 사용자 프로필 데이터를 LocalStorage에 저장 후, 필요 시 읽어와서 UI에 표시.

### localStorage 사용 방법

(1) 데이터 저장

- localStorage.setItem(key, value)를 사용하여 데이터를 저장한다.

```jsx
localStorage.setItem("username", "John");
```

(2) 데이터 가져오기

- localStorage.getItem(key)를 사용하여 데이터를 가져온다.

```jsx
const username = localStorage.getItem("username");
console.log(username); // "John"
```

(3) 데이터 삭제

- 특정 데이터를 삭제하려면 localStorage.removeItem(key)를 사용한다.

```jsx
localStorage.removeItem("username");
```

(4) 모든 데이터 삭제

- 모든 데이터를 삭제하려면 localStorage.clear()를 사용한다.

```jsx
localStorage.clear();
```

(5) 키 값 확인

- 특정 인덱스의 키를 확인하려면 localStorage.key(index)를 사용한다.

```jsx
const key = localStorage.key(0);
console.log(key); // 저장된 첫 번째 키
```

(6) 데이터 객체 저장

- localStorage는 문자열만 저장할 수 있으므로, 객체를 저장하려면 JSON.stringify를 사용하고, 가져올 때는 JSON.parse를 사용해야 한다.

```jsx
const user = { name: "John", age: 30 };
localStorage.setItem("user", JSON.stringify(user)); // 저장

const storedUser = JSON.parse(localStorage.getItem("user")); // 가져오기
console.log(storedUser.name); // "John"
```

### localStorage 사용 사례

(1) 사용자 인증 상태 유지  
사용자가 로그인한 후, 토큰이나 사용자 정보를 저장하여 인증 상태를 유지.

```jsx
localStorage.setItem("accessToken", "abc123");
const token = localStorage.getItem("accessToken");
```

(2) 사용자 설정 저장  
다크 모드, 언어 선택 등 사용자 설정을 저장.

```jsx
localStorage.setItem("theme", "dark");
const theme = localStorage.getItem("theme");
```

(3) 간단한 캐싱  
API 호출 결과를 저장하여 페이지 새로고침 시 데이터를 재사용.

```jsx
fetch("https://api.example.com/data")
  .then((response) => response.json())
  .then((data) => {
    localStorage.setItem("cachedData", JSON.stringify(data));
  });

const cachedData = JSON.parse(localStorage.getItem("cachedData"));
```

### localStorage의 장단점

장점

1. 간편한 사용

- 간단한 API로 브라우저에 데이터를 영구 저장할 수 있다.

2. 비교적 큰 용량

- 약 5MB까지 저장 가능.

3. HTTP 요청 없음

- 데이터를 서버로 전송하지 않아 네트워크 트래픽이 줄어듬.

4. 브라우저 간 일관성

- 같은 브라우저 내에서 데이터가 일관되게 유지된다.

단점

1. 보안 문제

- 데이터가 암호화되지 않으므로 민감한 정보를 저장하기에 적합하지 않음.
- 해결책:
  - HTTP-Only 쿠키나 세션 스토리지를 사용.
  - 민감한 데이터를 저장할 경우, 암호화를 적용.

2. 동기적 처리

- 모든 작업이 동기적으로 처리되므로, 큰 데이터를 저장하거나 가져올 때 성능 이슈가 발생할 수 있다.

3. 제한된 용량

- 5MB 제한으로 인해 대용량 데이터를 저장하기에는 적합하지 않다.

4. 브라우저 간 독립성

- 다른 브라우저에서는 저장된 데이터에 접근할 수 없다.

### localStorage 대신 다른 방법 사용

(1) sessionStorage

- sessionStorage는 브라우저 탭이 닫히면 데이터가 삭제된다.(일시적인 데이터 저장)
- 인증 상태를 유지해야 하는 시간이 짧거나 보안이 중요하지 않은 경우에 사용.

(2) 쿠키(Cookies)

- 쿠키는 서버와의 통신에 자동으로 포함되므로, CSRF(사이트 간 요청 위조) 보호가 필요한 상황에서 유용하다.
- 단, 쿠키는 용량이 작고(4KB 제한), 매 요청마다 서버로 전송되므로 성능에 영향을 줄 수 있다.

(3) 메모리 기반 저장소

- React의 useState나 Context와 같은 메모리 기반 저장소를 사용할 수도 있지만, 브라우저 새로고침 시 데이터가 초기화된다.

(4) 안전한 저장소

- 민감한 데이터(accessToken)는 보안상의 이유로 브라우저 저장소에 저장하기보다 HTTP-Only 쿠키를 사용하는 것이 더 안전하다.
- localStorage는 XSS(크로스 사이트 스크립팅) 공격에 취약하다. 이를 방지하려면 애플리케이션 보안에 신경 써야 한다.

### localStorage를 사용할 때 주의할 점

(1) 민감한 데이터 저장 금지  
localStorage는 클라이언트 측에서 쉽게 접근할 수 있으므로, 비밀번호와 같은 민감한 데이터는 저장하면 안된다.
accessToken도 최대한 짧은 유효기간을 설정하거나, 보안이 중요한 경우 쿠키를 대신 사용해야한다.

(2) XSS 공격 방지  
악의적인 스크립트가 localStorage에 저장된 데이터에 접근하지 못하도록 애플리케이션의 XSS 방어를 철저히 해야 한다.
보안 헤더(Content Security Policy 등)를 설정하거나, 데이터 입력 검증을 강화해야한다.

(3) 데이터 크기 제한  
localStorage는 보통 브라우저마다 약 5MB로 용량 제한이 있다.
너무 많은 데이터를 저장하지 않도록 주의해야한다.

---

## Context API란?

React의 Context API는 컴포넌트 간에 전역적으로 데이터를 공유하기 위한 기능이다.
일반적으로 부모-자식 관계를 따라 데이터를 전달해야 하지만, Context API를 사용하면 props를 깊게 전달할 필요 없이 데이터를 쉽게 공유할 수 있다.

`Context API의 구성 요소`

1. React.createContext()
   - Context 객체를 생성.
2. Provider
   - Context를 통해 제공할 데이터를 정의.
   - 트리 구조의 하위 컴포넌트에서 이 데이터를 사용할 수 있다.
3. Consumer
   - Context에서 제공한 데이터를 읽는 방법.
   - React 16.8 이후, useContext 훅을 주로 사용한다.

### Context API를 사용하는 이유

(1) Props Drilling 문제 해결

- 컴포넌트 트리에서 깊이 중첩된 자식에게 데이터를 전달하기 위해 중간 컴포넌트 필요 없이 데이터를 공유할 수 있다.

```jsx
// Props Drilling 예시
const App = () => <Parent data="전달할 데이터" />;
const Parent = ({ data }) => <Child data={data} />;
const Child = ({ data }) => <div>{data}</div>;
```

Context API를 사용하면 중간 컴포넌트를 거치지 않아도 된다.

(2) 전역 상태 관리

- 특정 데이터(예: 사용자 정보, 테마, 인증 상태 등)를 애플리케이션 전역에서 관리하고 싶을 때 유용하다.
- Redux와 같은 별도의 상태 관리 라이브러리를 사용하지 않고도 React에서 기본적으로 제공하는 Context API로 간단히 구현할 수 있다.

(3) 코드 가독성 향상

- 불필요한 props 전달이 줄어들고, 데이터 흐름을 더 명확히 파악할 수 있다.

### Context API 사용 방법

(1) Context 생성

- React의 createContext 메서드로 Context 객체를 생성.

```javascript
import React, { createContext } from "react";

// Context 생성
const MyContext = createContext();
```

(2) Provider 설정

- Context의 데이터를 제공할 컴포넌트에 Provider를 설정한다.
- Provider는 value라는 속성을 통해 데이터를 하위 컴포넌트로 전달한다.

```jsx
const App = () => {
  return (
    <MyContext.Provider value={{ user: "John", theme: "dark" }}>
      <Parent />
    </MyContext.Provider>
  );
};
```

(3) 데이터 소비

- 하위 컴포넌트에서 Context 데이터를 사용하려면 useContext 훅을 사용한다.

```jsx
import React, { useContext } from "react";

const Child = () => {
  const context = useContext(MyContext);
  return (
    <div>
      <p>User: {context.user}</p>
      <p>Theme: {context.theme}</p>
    </div>
  );
};
```

### Context API의 장단점

장점

1. Props Drilling 방지

- 데이터를 쉽게 공유할 수 있어 트리 구조가 간결해진다.

2. 내장 기능

- React의 기본 API로 추가 라이브러리 없이 사용 가능.

3. 전역 상태 관리

- 간단한 전역 상태 관리에 적합함.

단점

1. 복잡한 상태 관리

- 상태가 복잡하거나 업데이트 로직이 많을 경우 Redux와 같은 라이브러리가 더 적합할 수 있다.

2. 재렌더링 문제

- Context 값을 변경하면 해당 값을 사용하는 모든 컴포넌트가 리렌더링된다.
- 해결책:
  - Context를 여러 개로 나누거나, React.memo와 같은 최적화를 활용한다.

### Context API를 사용하는 경우

1. 테마 관리

- 다크 모드와 라이트 모드 같은 테마를 애플리케이션 전체에서 관리할 때.

2. 사용자 인증

- 로그인 상태, 사용자 정보, 인증 토큰 등을 전역에서 공유할 때.

3. 다국어 지원

- 언어 설정을 전역적으로 관리할 때.
