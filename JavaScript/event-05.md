# 마우스 오른쪽 클릭 금지하기 (2가지 방법)

1. return false 하기
2. preventDefault() 활용

마우스 오른쪽 버튼을 클릭했을 때,Context 메뉴가 뜨지 않도록 하는 방법.

## return false 하기

```html
<div oncontextmenu="return false">마우스 오른쪽 클릭</div>
```

- oncontextmenu 이벤트는 마우스 오른쪽을 클릭했을 때 발생한다.
- oncontextmenu가 호출되었을 때 return false 하면, 마우스 오른쪽을 클릭해도 context 메뉴가 열리지 않는다.

## preventDefault() 활용

```html
<div class="test">마우스 오른쪽 클릭</div>
```

```javascript
document
  .querySelector(".test")
  .addEventListener("contextmenu", (event) => event.preventDefault());
```

- 'test' div에 contextmenu 이벤트 등록.
- 이때 호출되는 event.preventDefault() 함수를 호출하면,
  해당 이벤트가 발생했을 때 발생했어야 하는 동작이 멈춘다.
