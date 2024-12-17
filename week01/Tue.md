### 오늘 배운 것

#### `<Fragment>`를 사용하는 것이 더 좋은 경우:

- 불필요한 DOM 노드를 피하고 싶을 때
- HTML 구조를 간결하게 유지하고 싶을 때
- 리스트 렌더링에서 그룹화가 필요한 경우. key 속성만 필요할 때.

#### `<div>`를 사용하는 것이 더 좋은 경우:

- CSS 스타일링이 필요하거나 특정 그룹에 class or id를 부여해야 할 때
- 의미 있는 HTML 태그가 필요한 경우 (예 :특정 그룹을 명확하게 구분하고 싶은 경우 div가 적합하다.)

\*Recap

- DOM 구조 간결성: `<Fragment>`
- 스타일링이나 의미가 필요한 경우: `<div>`

---

#### 이벤트 전파 (bubbling)

- 부여된 JSX 태그 내에서만 실행되는 `onScroll`을 제외한 React 내의 모든 이벤트는 전파된다.

#### 이벤트 전파 멈추기

- 이벤트 핸들러가 상위 태그에서 실행되지 않도록 멈추기 위해서는 e.stopPropagation()를 호출한다.

---

`컴포넌트 렌더링이 일어나는 두 가지 이유`  
(렌더링: 컴포넌트를 호출하는 것.)

1. 컴포넌트의 초기 렌더링인 경우
2. 컴포넌트의 state가 업데이트된 경우

렌더링을 트리거한 후 React는 컴포넌트를 호출하여 화면에 표시할 내용을 파악한다.

- 초기 렌더링에서 React는 루트 컴포넌트를 호출한다.
- 이후 렌더링에서 React는 state 업데이트가 일어나 렌더링을 트리거한 컴포넌트를 호출한다.

재귀적 단계: 업데이트된 컴포넌트가 다른 컴포넌트를 반환하면 React는 다음으로 해당 컴포넌트를 렌더링하고 해당 컴포넌트도 컴포넌트를 반환하면 반환된 컴포넌트를 다음에 렌더링하는 방식이다.
중첩된 컴포넌트가 더 이상 없고 React가 화면에 표시되어야 할 내용을 정확히 알 때까지 이 단계는 계속된다.

컴포넌트를 렌더링(호출)한 후 React는 DOM을 수정한다.

- 초기 렌더링의 경우 React는 appendChild() DOM API를 사용하여 생성한 모든 DOM 노드를 화면에 표시한다.
- 리렌더링의 경우 React는 필요한 최소한의 작업(렌더링하는 동안 계산된 것!)을 적용하여 DOM이 최신 렌더링 출력과 일치하도록 한다.
  React는 렌더링 간에 차이가 있는 경우에만 DOM 노드를 변경한다.

`React가 컴포넌트를 다시 렌더링할 때.`

1. React가 함수를 다시 호출한다.
2. 함수가 새로운 JSX 스냅샷을 반환한다.
3. 그러면 React는 함수가 반환한 스냅샷과 일치하도록 화면을 업데이트한다.

---

#### 전개 문법으로 객체 복사하기

```javascript
const [person, setPerson] = useState({
  firstName: "Barbara",
  lastName: "Hepworth",
  email: "bhepworth@sculpture.com",
});
```
해당 폼에서 email필드만 수정하고 나머지 모든 필드는 이전 값 유지하기

```javascript
setPerson({
  ...person, // 이전 필드를 복사
  email: e.target.value // 새로운 부분은 덮어쓰기
})
```
* ... 전개 문법은 '얕은 복사'

#### 중첩된 객체 구조 변경
```javascript
const [person, setPerson] = useState({
  name: 'Niki de Saint Phalle',
  artwork: {
    title: 'Blue Nana',
    city: 'Hamburg',
    image: 'https://i.imgur.com/Sd1AgUOm.jpg',
  }
});
```
person.artwork.city 업데이트하기
```javascript
setPerson({
  ...person, // 다른 필드 복사
  artwork:{ // artwork 교체
    ...person.artwork, // 동일한 값 사용
    city: 'New Delhi', // city만 New Delhi로 변경
  }
})
```

#### 반복적인 복사 코드를 줄이기 위해 Immer 사용하기
[Immer로 간결한 갱신 로직 작성하기 ](https://ko.react.dev/learn/updating-objects-in-state)  
[immer: github](https://github.com/immerjs/use-immer)

Immer가 제공하는 `draft`는 Proxy라고 하는 아주 특별한 객체 타입으로, 당신이 하는 일을 “기록” 한다. 객체를 원하는 만큼 자유롭게 변경할 수 있다. Immer는 내부적으로 draft의 어느 부분이 변경되었는지 알아내어, 변경사항을 포함한 완전히 새로운 객체를 생성한다.