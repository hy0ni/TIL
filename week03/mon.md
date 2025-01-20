### reducer

reducer는 컴퓨터의 계산기처럼 작동한다.

- 현재 상태(state)와
- 어떤 일을 할지 설명한 액션(action)
  이 두 가지를 입력받아, 새로운 상태를 반환한다.

예를 들어 친구와 점심 메뉴를 고르려고 한다고 가정해보면,

1. 현재 상태: '점심 메뉴를 아직 못 정했음.'
2. 친구의 요청(액션): '피자를 먹고 싶다.'
3. 새로운 상태: '피자를 먹기로 함'

```javascript
function reducer(state, action) {
  if (action.type === "피자") {
    return "피자를 먹기로 함";
  } else if (action.type === "햄버거") {
    return "햄버거를 먹기로 함";
  }
  return state; // 아무 일도 없으면 현재 상태 유지
}
```

(1)카운터를 만들고 싶다고 가정해본다면:

- 상태(state): 숫자(카운트 값)
- 액션(action): '증가', '감소', '리셋'

```javascript
function counterReducer(state, action) {
  switch (action.type) {
    case "증가": // 액션이 '증가'일 때
      return state + 1;
    case "감소": // 액션이 '감소'일 때
      return state - 1;
    case "리셋": // 액션이 '리셋'일 때
      return 0;
    default: // 다른 액션은 처리하지 않음
      return state;
  }
}
```

(2)useReducer훅 사용

```javascript
import React, { useReducer } from "react";

function counterReducer(state, action) {
  switch (action.type) {
    case "증가":
      return state + 1;
    case "감소":
      return state - 1;
    case "리셋":
      return 0;
    default:
      return state;
  }
}

function Counter() {
  const [count, dispatch] = useReducer(counterReducer, 0); // 초기 상태는 0

  return (
    <div>
      <p>현재 카운트: {count}</p>
      <button onClick={() => dispatch({ type: "증가" })}>+1</button>
      <button onClick={() => dispatch({ type: "감소" })}>-1</button>
      <button onClick={() => dispatch({ type: "리셋" })}>리셋</button>
    </div>
  );
}

export default Counter;
```

- `dispatch`는 리듀서에게 액션을 전달하는 '명령 버튼'이다.
- 예를 들어, dispatch({ type: '증가' })를 호출하면:
  - 현재 상태와 함께 리듀서가 호출된다.
  - 리듀서가 새로운 상태를 계산한다.
- 새로운 상태가 count에 저장되어 화면이 다시 렌더링된다.

#### reducer를 사용하는 이유

복잡한 상태 로직 관리에 유용하다.

- useState로 관리하기 어려운 여러 상태를 깔끔하게 관리할 수 있다.
- 예를 들어, To-Do 리스트 처럼 여러 개의 상태가 서로 연관된 경우에 유용하다.

```javascript
function todoReducer(state, action) {
  switch (action.type) {
    case "추가":
      return [...state, action.payload];
    case "삭제":
      return state.filter((todo) => todo.id !== action.payload.id);
    case "수정":
      return state.map((todo) =>
        todo.id === action.payload.id
          ? { ...todo, text: action.payload.text }
          : todo
      );
    default:
      return state;
  }
}
```
`Recap`  
1. reducer는 현재 상태와 액션을 받아 새로운 상태를 반환한다.
2. useReducer는 컴포넌트 안에서 리듀서를 사용하게 해준다.
3. 복잡한 상태 관리에 적합하며, 상태 변화 로직을 깔끔하게 관리할 수 있다.

[state 로직을 reducer로 작성하기](https://ko.react.dev/learn/extracting-state-logic-into-a-reducer)



## Reducer

reducer는 state를 다루는 다른 방법이다.  
컴포넌트가 커질수록 그 안에서 state를 다루는 로직의 양도 늘어나게 되는데,
복잡성은 줄이고 접근성을 높이기 위해 컴포넌트 내부에 있는 state로직을 컴포넌트 외부의 reducer라고 하는 단일 함수로 옮길 수 있다.

### useState에서 useReducer로 바꾸는 방법

1. state를 설정하는 것에서 action을 dispatch 함수로 전달하는 것으로 바꾸기.
2. reducer 함수 작성하기.
   reducer 함수는 state에 대한 로직을 넣는 곳이다. 이 함수는 현재의 state 값과 action 객체, 이렇게 두개의 인자를 받고 다음 state 값을 반환한다.

```javascript
function yourReducer(state, action) {
  // React가 설정하게될 다음 state 값을 반환합니다.
}
```

3. 컴포넌트에서 reducer 사용하기.

### Step 1: useState를 사용한 코드

```javascript
import { useState } from "react";

function UserForm() {
  const [name, setName] = useState("");
  const [age, setAge] = useState("");

  const handleNameChange = (e) => setName(e.target.value);
  const handleAgeChange = (e) => setAge(e.target.value);

  const handleReset = () => {
    setName("");
    setAge("");
  };

  return (
    <div>
      <input
        type="text"
        placeholder="Name"
        value={name}
        onChange={handleNameChange}
      />
      <input
        type="number"
        placeholder="Age"
        value={age}
        onChange={handleAgeChange}
      />
      <button onClick={handleReset}>Reset</button>
      <p>
        Name: {name}, Age: {age}
      </p>
    </div>
  );
}

export default UserForm;
```

### Step 2: useReducer로 변환

`useReducer hook`은 두 개의 인자를 넘겨받는다.

1. reducer 함수
2. 초기 state 값

그리고 아래와 같이 반환한다.

1. state를 담을 수 있는 값
2. dispatch 함수 (사용자의 action을 reducer 함수에게 “전달하게 될”)

```javascript
import { useReducer } from "react";

const initialState = {
  name: "",
  age: "",
};

function reducer(state, action) {
  switch (action.type) {
    case "SET_NAME":
      return { ...state, name: action.payload };
    case "SET_AGE":
      return { ...state, age: action.payload };
    case "RESET":
      return initialState;
    default:
      throw new Error("Unhandled action type: " + action.type);
  }
}
function Reducer() {
  const [state, dispatch] = useReducer(reducer, initialState);

  const handleNameChange = (e) => {
    dispatch({ type: "SET_NAME", payload: e.target.value });
  };
  const handleAgeChange = (e) => {
    dispatch({ type: "SET_AGE", payload: e.target.value });
  };
  const handleReset = () => {
    dispatch({ type: "RESET" });
  };
  return (
    <div>
      <input
        type="text"
        placeholder="Name"
        value={state.name}
        onChange={handleNameChange}
      />
      <input
        type="number"
        placeholder="Age"
        value={state.age}
        onChange={handleAgeChange}
      />
      <button onClick={handleReset}>Reset</button>
      <p>
        Name: {state.name} / Age: {state.age}
      </p>
    </div>
  );
}
```

1. state를 action으로 전달: useState로 개별적으로 관리하던 name과 age를 하나의 state로 통합한다.
2. reducer 함수 작성: 상태 업데이트를 처리하는 reducer 함수를 작성한다.
3. 컴포넌트에서 useReducer 사용: useReducer를 사용하여 상태 관리 로직을 적용한다.

**dispatch** 함수에 넣어준 객체를 “action”이라고 한다.
action 객체는 어떤 형태든 될 수 있지만, 발생한 일을 설명하는 문자열 type을 넘겨주고 이외의 정보는 다른 필드에 담아서 전달하도록 작성하는게 일반적이다.
type은 컴포넌트에 따라 값이 다르며 무슨 일어나는지를 설명할 수 있는 이름을 넣어주면 된다.

**payload**는 액션에 추가적인 데이터를 담기 위해 사용하는 속성이다.
payload는 리듀서 함수가 상태를 업데이트하는데 추가 정보가 필요할 경우 사용하며, 이름 그대로 '전달되는 데이터'를 의미한다. (필요하지 않은 경우 생략 가능)

액션의 구조

```javascript
{
  type: 'SET_TEXT',    // 상태를 변경하기 위한 액션의 유형
  payload: 'New Text'  // 상태를 업데이트할 데이터
}
```

- reducer 함수는 state를 인자로 받고 있기 때문에, 이를 **컴포넌트 외부에서 선언**할 수 있다.
- reducer 함수 안에서는 switch 문을 사용하는 게 규칙이다.

`useState를 사용할 때`

- 상태가 단순하고 독립적일 때.
- 코드가 간결하고 빠르게 작성되어야 할 때.

`useReducer를 사용할 때`

- 상태가 복잡하거나 여러 상태가 밀접하게 관련되어 있을 때.
- 상태 관리 로직을 분리하거나 디버깅 및 테스트를 쉽게 하고 싶을 때.

`좋은 Reducer 작성 습관`

- 순수 함수로 작성: 입력 값이 같다면 출력 값도 항상 같아야 함.
- 사이드 이펙트(요청, 타이머 등)를 포함하지 말 것.
- 객체나 배열을 직접 수정하지 않고 불변성 유지(새로운 객체x,배열 생성x).
- 각 action은 데이터 안에서 여러 변경들이 있더라도 하나의 사용자 상호작용을 설명해야 한다.
- 복잡한 상태 업데이트(예: 여러 필드 변경)는 여러 action 대신 하나의 action으로 처리하는 것이 효율적이다.
- 여러 필드 변경을 하나로 묶어서 처리할 때 의미 있는 액션 이름을 사용해야 한다.
  (디버깅 시 어떤 액션이 어떤 순서로 실행되었는지 쉽게 추적 가능.)
