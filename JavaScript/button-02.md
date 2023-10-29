# 버튼 활성화/비활성화 하기

- input 태그의 disabled 속성
- fieldset 전체 버튼 비활성화 하기
- javascript로 활성화/비활성화 설정

## input 태그의 disabled 속성

HTML의 `<input type='button'>` 태그를 사용한 버튼을 활성화/비활성화 할때는 disabled 속성을 사용한다.

```html
<input type="button" value="활성화" />
<input type="button" disabled value="비활성화1" />
<input type="button" disabled="disabled" value="비활성화2" />
```

<input type='button' value='활성화' />

기본적으로 input 태그에 disabled 속성을 따로 명시해 주지 않으면, 버튼은 활성화된다.

<input type='button' disabled value='비활성화1' />
input 태그에 disabled 속성을 명시해 주면, 버튼이 비활성화된다.

<input type='button' disabled='disabled' value='비활성화2'/>

disabled 속성에 어떤 값을 주면, 버튼은 활성화되게 되는데
disabled 속성에 값을 주면서, 버튼을 비활성화하고 싶다면 'disabled'라고 명시해 줘야 한다.

## fieldset 전체 버튼 비활성화 하기

```html
<fieldset disabled>
  <legend>Fieldset Button</legend>
  <input id="targeBtn1" type="button" value="버튼1" />
  <input id="targeBtn2" type="button" value="버튼2" />
</fieldset>
```

fieldset 안의 버튼들은 각각의 버튼에 disabled 속성을 주어서 비활성화할 수도 있지만,
fieldset에 disabled 속성을 주면,
fieldset 안의 모든 버튼이 비활성화된다.

## javascript로 활성화/비활성화 설정

```html
<input id="targeBtn" type="button" disabled value="버튼" />
```

```javascript
const target = document.querySelector("#targeBtn");
target.disabled = false; // 활성화
```

disabled 값이 true라면 버튼이 비활성화되고, false라면 활성화
