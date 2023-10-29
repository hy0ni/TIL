# 이벤트 한번만 실행되도록 하기

등록된 이벤트가 한번만 실행되도록 하기 위해서는
addEventListener() 함수를 사용하여 이벤트를 등록할 때 once 옵션을 추가해 주면 된다.

## addEventListener()의 once 옵션 사용하기

```javascript
addEventListener(type, listener, options);
```

**`options`**: 이벤트 리스너에 대한 특성을 지정하는 객체

**`once`**: listener가 추가된 후 최대 한 번 호출되어야 함을 나타내는 Boolean 값. true인 경우 호출 시 리스너가 자동으로 제거된다.
listener 지정하지 않으면 기본값은 false.

```html
<button type="button" class="btn">한번만 실행</button>
```

```javascript
const $btn = document.querySelector(".btn");

$btn.addEventListener(
  "click",
  () => {
    console.log("hello");
  },
  { once: true }
);
```

버튼을 클릭했을 때, 한 번만 동작하도록 하기 위해
addEventListener() 메서드의 3번째 파라미터로
{ once : true } 객체를 전달한다.
