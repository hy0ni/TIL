# 이벤트 추가, 제거하기

- addEventListener() 이벤트 추가
- removeEventListener() 이벤트 제거

## addEventListener() 이벤트 추가

`EventTarget: addEventListener() method`

addEventListener() 메서드는 지정된 EventTarget이벤트가 대상에 전달될 때마다 호출되는 함수를 설정한다.

```javascript
element.addEventListener(type, listener);
```

- type : 이벤트 타입
- listener : 이벤트가 발생했을 때 실행할 함수

```html
<h1 id="title">hello</h1>
```

```javascript
const $h1 = document.getElementById("title");

function greeting() {
  console.log("hello");
}

$h1.addEventListener("click", greeting);
```

클릭 이벤트가 발생하면 "hello" 문자가 콘솔창에 출력됨.

## removeEventListener() 이벤트 제거

`EventTarget: removeEventListener() method`

EventTarget.addEventListener()로 등록된 이벤트 리스너를 대상에서 제거한다.

```javascript
element.removeEventListener(type, listener);
```

```javascript
const $h1 = document.getElementById("title");

// 이벤트 삭제 X
$h1.addEventListener("click", () => {
  console.log("hello");
});

// 이벤트 삭제 O
function greeting() {
  console.log("hello");
}

$h1.addEventListener("click", greeting);
$h1.removeEventListener("click", greeting);
```

addEventListener() 메서드를 사용하여 이벤트를 등록할 때,
2번째 파라미터로 전달하는 eventListener를 익명함수로 전달하게 되면 removeEventListener() 메서드를 사용해 이벤트를 삭제할 수 없다.

removeEventListener() 메서드를 호출할 때 2번째 파라미터로 삭제할 이벤트 함수를 넣어줘야 하기 때문이다.
