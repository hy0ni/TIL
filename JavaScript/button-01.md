# 버튼 이름 변경하기 (버튼 클릭)

HTML로 이미 정의한 버튼의 이름을 이벤트가 발생했을 때 변경하는 방법.

- `<input type='button' />`일 경우
- `<button></button>`일 경우

## `<input type='button' />`일 경우

`<input type='button' />` 클릭했을 때, 버튼의 이름을 변경하기.

```html
<input type="button" class="btn" value="클릭!!" />
```

```javascript
const $btn = document.querySelector(".btn");

$btn.addEventListener("click", () => {
  $btn.value = "새이름!";
});
```

버튼이 `<input type='button' />`으로 정의된 경우
element의 `value 값을 변경`하여, 버튼 이름을 변경한다.

## `<button></button>` 일 경우

`<button></button>` 클릭했을 때, 버튼의 이름을 변경하기.

```html
<button class="btn">클릭!!</button>
```

```javascript
const $btn = document.querySelector(".btn");

$btn.addEventListener("click", () => {
  $btn.innerText = "새이름!";
});
```

버튼이 `<button></button>`으로 정의된 경우
element의 `innerText 속성을 변경`하여, 버튼 이름을 변경한다.

button 태그를 사용하여 버튼을 정의한 경우에는
element의 innerHTML 속성에 HTML 태그를 지정하여
버튼 안 텍스트의 스타일을 정의하거나 변경해 줄 수도 있다.
