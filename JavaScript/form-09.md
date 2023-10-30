# 라디오 버튼 클릭하여, 텍스트 값 출력하기

라디오 버튼을 label 태그와 연결하고,  
라디오 버튼을 클릭 시 label 태그에 정의된 텍스트 값을 가져와서 출력하는 방법.

```html
<input type="radio" name="gender" value="female" id="female" onclick="getRadioText(event)" />
<label for="female">여성</label>

<input type="radio" name="gender" value="male" id="male" onclick="getRadioText(event)" />
<label for="male">남성</label>

<div id="result"></div>
```

라디오 버튼을 클릭하면 'getRadioText(event)' 함수 호출.

```javascript
function getRadioText(event) {
  const radioId = event.target.id;
  const query = `label[for="${radioId}"]`;
  const text = document.querySelector(query).innerText;

  document.getElementById("result").innerText = text;
}
```

`event.target.id;`  
선택된 라디오 버튼의 id  
id로 label 태그의 'for' 속성값이 'radioId'인 element를 찾고,  
그 element의 텍스트 값을 찾는다.

``label[for="${radioId}"]`;`  
query를 querySelector()의 파라미터로 전달하여,  
label 태그 중, 'for' 속성이 'radioId'인 element를 찾음.

`document.getElementById("result").innerText = text;`  
document.querySelector() 함수는  
DOM에서 query 조건을 만족하는 element 중 가장 첫 번째 element를 리턴한다.  
query를 querySelector()의 파라미터로 전달하면  
조건에 맞는 label element 하나를 찾을 것이고,  
그 element의 텍스트 값을 innerText로 가져온다.
