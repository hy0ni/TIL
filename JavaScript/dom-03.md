# innerHTML, innerText, textContent 차이점

```html
<div class="content">
  hello       world
  <span style="display:none">숨겨진 텍스트</span>
</div>
```

```javascript
let $elm = document.querySelector(".content");

console.log($elm.innerText); // hello world

console.log($elm.innerHTML);
//  hello       world
// <span style="display:none">숨겨진 텍스트</span>

console.log($elm.textContent);
//  hello       world
// 숨겨진 텍스트
```

## innerHTML

innerHTML은 'Element'의 속성으로, 해당 Element의 HTML, XML을 읽어오거나, 설정할 수 있다.

div 안에 있는 HTML 전체 내용 그대로를 가져온다.

## innerText

innerText는 'Element'의 속성으로, 해당 Element 내에서 사용자에게 '보여지는' 텍스트 값을 읽어온다.

'hello world'라고 입력되어 있지만,
브라우저가 사용자에게 이 내용을 보여줄 때는, 연속되는 공백은 무시하고 하나의 공백만 처리하여 보여준다.

## textContent

textContent는 'Node'의 속성으로,
innetText와는 달리 script나 style 태그와 상관없이
해상 노드가 가지고 있는 텍스트 값을 그대로 읽는다.

'hello world' 연속된 공백이 그대로 표현됨.
'display:none' 스타일이 적용된 '숨겨진 텍스트' 문자열도 그대로 출력됨.

innerHTML, innerText, textContent 이 세 가지 속성은
일반 Text 값을 가지고 올 때는 별 차이가 없지만,
element가 가지고 있는 콘텐츠의 내용에 따라서 차이가 있다.
