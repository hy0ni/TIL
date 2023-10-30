# input 박스에 영어만 입력되게 하기 (2가지 방법)

- [input 박스에 영어만 입력되게 하기 (2가지 방법)](#input-박스에-영어만-입력되게-하기-2가지-방법)
  - [oninput 이벤트, 정규식, replace() 함수 사용하기](#oninput-이벤트-정규식-replace-함수-사용하기)
  - [pattern 속성에 정규식 적용하기](#pattern-속성에-정규식-적용하기)

## oninput 이벤트, 정규식, replace() 함수 사용하기

```html
<input type="text" oninput="handleOnInput(this)" />
```

```javascript
function handleOnInput(e) {
  e.value = e.value.replace(/[^A-Za-z]/gi, "");
}
```

알파벳이 아닌 다른 값을 입력하면 아예 입력이 되지 않는다.  
input에 사용자가 값을 입력하면 handleOnInput 함수를 실행됨.

이 함수는 사용자가 입력한 값을 replace함수와 정규식을 활용하여  
입력한 값에 알파벳이 아닌 문자가 있는 경우 공백으로 변환시켜서 input에 다시 넣어준다.

## pattern 속성에 정규식 적용하기

```html
<form>
  <input type="text" pattern="[A-Za-z]+" />
  <input type="submit" />
</form>
```

```css
input:invalid {
  border: 4px solid red;
}
```

'pattern' 속성에 정규식 적용.

사용자가 알파벳이 아닌 값을 입력하고,  
'제출(submit)' 버튼을 클릭하면 메시지를 출력하고, submit을 제한한다.

CSS에 'input:invalid' 속성을 적용하면  
사용자가 패턴에 맞지 않는 값을 입력할 경우  
CSS를 변경하여 '제출' 버튼 클릭전에도 사용자에게 메시지를 줄 수 있다.
