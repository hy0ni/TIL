### 오늘 공부한 것

#### reducer

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
