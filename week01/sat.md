### 오늘 공부한 것

#### 객체 State 업데이트하기

- state는 객체를 포함한 모든 종류의 자바스크립트 값을 가질 수 있다.
- state가 가진 객체를 직접 변경x
- 객체를 변경하는 대신 교체해야 한다.
- 객체를 업데이트하고 싶은 경우 새로운 객체를 생성하여(또는 기존 객체의 복사본 만들기), state가 복사본을 사용하도록 해야한다.
- 자바스크립트 값들은 변경할 수 없거나 '읽기 전용'을 의미하는 `'불변성'`을 가진다. 값을 교체하기 위해서는 리렌더링이 필요하다.
- 객체를 복사하지 않고 직접 수정하면 React에서 상태 변경 감지가 어려울 수 있으므로 항상 불변성을 유지하며 상태를 업데이트해야 한다.

`전개 문법으로 객체 복사하기`  
새로 생성하는 객체에 존재하는 데이터를 포함하고 싶은 경우(예를 들어 폼에서 단 한개의 필드만 수정하고, 나머지 모든 필드는 이전 값을 유지하고 싶은 경우)

```javascript
const [person, setPerson] = useState({
  firstName: "Barbara",
  lastName: "Hepworth",
  email: "bhepworth@sculpture.com",
});

setPerson({
  firstName: e.target.value, // input의 새로운 first name
  lastName: person.lastName,
  email: person.email,
});
```

`... 객체 전개 구문 사용하기`

```javascript
setPerson({
  ...person, // 이전 필드를 복사
  firstName: e.target.value, // 새로운 부분은 덮어쓰기
});
```

... 객체 전개 구문을 사용하면 모든 프로퍼티를 각각 복사하지 않아도 된다.

- ... 전개 문법은 '얕다'. 한 레벨 깊이의 내용만 복사된다. 즉 중첩된 프로퍼티를 업데이트하고 싶다면 한 번 이상 사용해야 한다.

`중첩된 객체 갱신하기`
setPerson을 사용하여 상태를 업데이트할 때, 객체와 객체 내부의 중첩된 값을 안전하게 복사하여 특정 부분만 변경하기.

```javascript
const [person, setPerson] = useState({
  name: "Niki de Saint Phalle",
  artwork: {
    title: "Blue Nana",
    city: "Hamburg",
    image: "https://i.imgur.com/Sd1AgUOm.jpg",
  },
});

setPerson({
  ...person, // person 객체 복사
  artwork: {
    ...person.artwork, // artwork 객체를 복사
    city: "New Delhi", // city 속성만 업데이트
  },
});
```
React에서는 상태를 직접 수정하는 대신, 기존 상태를 복사한 뒤 변경해야 한다.
하지만 깊게 중첩된 객체가 많아질수록 코드가 복잡해질 수 있다.

`Immer로 간결한 갱신 로직 작성하기`
state가 깊이 중첩되어있다면 `평탄화`를 고려해야한다. immer는 변경 구문을 사용할 수 있게 해주며 복사본 생성을 도와주는 라이브러리다.

immer를 사용할 경우, 기존 상태는 그대로 유지되며, 새로운 상태만 반환된다.
- 불변성 유지: 기존 상태는 절대 변경되지 않는다.
- 효율성: 내부적으로는 복사가 필요할 때만 수행하므로 성능에 유리하다.

```javascript
updatePerson((draft) => {
  draft.artwork.city = "Lagos";
});
```

immer가 제공하는 `draft`는 Proxy라고 하는 아주 특별한 객체 타입으로 immer는 내부적으로 draft의 어느 부분이 변경되었는지 알아내어, 변경사항을 포함한 완전히 새로운 객체를 생성한다.