### 오늘 공부한 것

#### 배열 state 업데이트하기

state에 저장된 배열을 업데이트하고 싶은 경우, 객체와 마찬가지로 새 배열을 생성(혹은 기존 배열의 복사본을 생성)한 뒤, 새 배열을 state로 업데이트 해야 한다.

- 배열은 읽기 전용으로 처리해야한다.
- 즉 arr[0] = 'bird'처럼 배열 내부의 항목을 재할당해서는 안되며 push()나 pop()같은 함수로 배열을 변경해서는 안된다.
- 배열을 업데이트할 때마다 새 배열을 state 설정 함수에 전달해야 한다.
- 원본 배열을 변경시키지 않는 filter()와 map()같은 함수를 사용하여 원본 배열을 복사한 새 배열을 state에 설정해야 한다.
- 추가: push, unshift(배열을 변경) 대신 `concat, [...arr]전개 연산자`(새 배열을 반환) 사용.
- 제거: pop, shift, splice(배열을 변경) 대신 `filter, slice`(새 배열을 반환) 사용.
- 교체: splice, arr[i] = ...할당(배열을 변경) 대신 `map`(새 배열을 반환) 사용.
- 정렬: reverse, sort(배열을 변경)는 배열을 복사한 이후 처리.
- 또는 두 열의 함수를 모두 사용할 수 있는 immer를 사용.

`배열에 항목 추가하기`

```javascript
const [artists, setArtists] = useState([]);

setArtists(
  // 아래의 새로운 배열로 state를 변경합니다.
  [
    ...artists, // 기존 배열의 모든 항목
    { id: nextId++, name: name }, // 마지막에 새 항목을 추가
  ]
);

setArtists([
  { id: nextId++, name: name }, // 추가할 항목을 앞에 배치하고,
  ...artists, // 기존 배열의 항목들을 뒤에 배치
]);
```

`배열에서 항목 제거하기`  
배열에서 항목을 제거하는 가장 쉬운 방법은 filter 함수를 사용해 필터링하는 것이다. 즉 해당 항목을 포함하지 않는 새 배열을 반환.

```html
<button
  onClick={() => {
    setArtists(artists.filter((a) => a.id !== artist.id));
  }}
>
  Delete
</button>;
```

artists.id와 ID가 다른 artists로 구성된 배열을 생성. 즉, 각 artist의 Delete 버튼은 해당 artist를 배열에서 필터링한 다음, 반환된 배열로 리렌더링을 요청한다. filter는 원본 배열을 수정하지 않는다.

`배열 변환하기`  
배열의 일부 또는 전체 항목을 변경하고자 한다면, map()을 사용해 새로운 배열을 만들 수 있다.

`배열 내 항목 교체하기`  
배열에서 하나 이상의 항목을 교체하기 위해서는 map()을 사용하는 편이 좋다.
항목을 교체하기 위해 map()을 이용해 새로운 배열을 만든다.

`배열에 항목 삽입하기`  
시작이나 끝이 아닌 위치에 항목을 삽입하고 싶은 경우
slice() 함수를 사용하여 배열의 '일부분'을 잘라낸다. 삽입 지점 앞에 자른 배열을 ...전개하고 새 항목과 원본 배열의 나머지 부분을 전개하는 배열로 만든다.

```javascript
const nextArtists = [
  const insertAt = 1; // 인덱스
  // 삽입 지점 이전 항목
  ...artists.slice(0, insertAt),
  // 새 항목
  { id: nextId++, name: name },
  // 삽입 지점 이후 항목
  ...artists.slice(insertAt),
];
setArtists(nextArtists);
```

`배열에 기타 변경 적용하기`  
전개 구문과 map(), filter() 같은 비-변경 함수들만으로 할 수 없는 일이 몇 가지 있다. 예를 들어 배열을 뒤집거나 정렬하고 싶은 경우이다.
JavaScript의 reverse() 및 sort() 함수는 원본 배열을 변경시키므로 직접 사용할 수 없다.
대신, 먼저 배열을 복사한 뒤 변경할 수 있다.

```javascript
const nextList = [...list];
nextList.reverse();
setList(nextList);
```

- [...list] 전개 구문을 사용해 원본 배열의 복사본을 만든다.
- 복사본이 있으므로 nextList.reverse() 또는 nextList.sort()와 같은 변경 함수를 사용할 수 있다.
- 배열을 복사하더라도 배열 내부에 기존 항목을 직접 변경해서는 안된다. 이는 얕은 복사이기 때문에 복사한 새 배열에는 원본 배열과 동일한 항목이 포함된다. 따라서 복사된 배열 내부의 객체를 수정하면 기존 state가 변경된다.

`배열 내부의 객체 업데이트하기`  
객체는 실제로 배열 '내부'에 위치하지 않는다. 배열의 각 객체는 배열이 '가리키는' 별도의 값이다.
중첩된 state를 업데이트할 때, 업데이트하려는 지점부터 최상위 레벨까지의 복사본을 만들어야 한다.

map을 사용하면 이전 항목의 변경 없이 업데이트된 버전으로 대체할 수 있다.

```javascript
const initialList = [
  { id: 0, title: "Big Bellies", seen: false },
  { id: 1, title: "Lunar Landscape", seen: false },
  { id: 2, title: "Terracotta Army", seen: true },
];

const [myList, setMyList] = useState(initialList);

setMyList(
  myList.map((artwork) => {
    if (artwork.id === artworkId) {
      // 변경된 새 객체를 만들어 반환
      return { ...artwork, seen: nextSeen };
    } else {
      // 변경시키지 않고 반환
      return artwork;
    }
  })
);
```

`immer 사용하기`

```javascript
import { useImmer } from "use-immer";

export default function BucketList() {
  const [myList, updateMyList] = useImmer(initialList);

updateMyTodos(draft => {
  const artwork = draft.find(a => a.id === artworkId);
  artwork.seen = nextSeen;
});
```

Immer를 사용하면 artwork.seen = nextSeen과 같이 변경 가능하다.
원본 state가 변경되는 것이 아닌, immer에서 제공하는 특수 draft 객체를 변경하기 때문이다.
push()와 pop()같은 변경 함수들도 draft의 컨텐츠에 적용할 수 있다.
내부적으로 Immer는 항상 draft에서 수행한 변경 사항에 따라 처음부터 다음 state를 구성한다. 이렇게 하면 state를 변경하지 않고도 이벤트 핸들러를 매우 간결하게 유지할 수 있다.

`*Recap`

- 배열을 state로 만들 수 있지만 변경하면 안된다.
- 배열을 변경하는 대신 배열의 복사본을 만들고, state를 업데이트 해야한다.
- [...arr, newItem] 배열 전개 구문을 새용해 새 항목을 포함한 배열을 생성할 수 있다.
- filter()와 map()을 사용하여 필터링된 항목들이나 변환된 항목들을 가진 배열을 만들 수 있다.
- immer를 사용하여 코드 간결성을 유지할 수 있다.
