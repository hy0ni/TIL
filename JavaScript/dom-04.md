# element 생성, 삭제, 숨기기

## element.appendChild()

`element.appendChild()` 함수를 이용하여, 앞에서 생성한 텍스트 노드를 기존의 element에 추가한다.

## Document.createElement()

```javascript
const createDiv = document.createElement("div");
document.body.appendChild(createDiv);
```

HTML 문서에서, Document.createElement() 메서드는 지정한 tagName의 HTML 요소를 만들어 반환한다.

## Document.createTextNode()

```javascript
const createText = document.createTextNode("hello world");
document.body.appendChild(createText);
```

텍스트 노드를 생성한다.

## element.remove()

```html
<div class="content"></div>
```

```javascript
const $div = document.querySelector(".content");
$div.remove();
```

element를 삭제하기 위해서는,
삭제하려는 element를 선택하고, remove() 함수를 호출한다.

## element 숨기기

### style.display 속성 사용하기

```html
<div class="content">hello</div>
```

```javascript
const $div = document.querySelector(".content");
$div.style.display = "none";
```

display 기본 값 'block'
$div.style.display 값을 'block', 'none'으로 설정함.
display를 none으로 설정하면 div 영역 자체가 숨겨진다.

### style.visibility 속성 사용하기

```html
<div class="content">hello</div>
```

```javascript
const $div = document.querySelector(".content");
$div.style.visibility = "hidden";
```

visibility 기본 값 'visible'
display 속성 대신 visibility 속성을 사용하면,
div가 'hidden'이 되더라도 원래 div가 있던 영역은 그대로 유지된다.
