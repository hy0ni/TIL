# 라디오 버튼(radio) 값 가져와서 출력하기

- 라디오 클릭 시, 클릭한 값 바로 출력하기
- 라디오 버튼 값을 선택한 후, 출력 버튼 클릭 시 값 출력하기

## 라디오 클릭 시, 클릭한 값 바로 출력하기

```html
<input type="radio" name="gender" value="female" onclick="getGender(event)" />여성
<input type="radio" name="gender" value="male" onclick="getGender(event)" />남성
<div id="result"></div>
```

각각의 라디오 버튼은 onclick 이벤트가 발생했을 때 getGender()라는 함수를 호출한다.  
event 객체를 파라미터로 넘겨준다.

```javascript
function getGender(event) {
  document.getElementById("result").innerText = event.target.value;
}
```

라디오 버튼 클릭 시 발생하는 event 객체를 파라미터로 받아서  
event.target.value 값을 div#result에 출력함.

## 라디오 버튼 값을 선택한 후, 출력 버튼 클릭 시 값 출력하기

```html
<input type="radio" name="gender" value="female" />여성
<input type="radio" name="gender" value="male" />남성
<button onclick="getGender()">확인</button>
```

'확인' 버튼을 클릭했을 때, 'getGender()' 함수 호출.

```javascript
function getGender() {
  const genderNodeList = document.getElementsByName("gender");

  genderNodeList.forEach((node) => {
    if (node.checked) {
      document.getElementById("result").innerText = node.value;
    }
  });
}
```

`const genderNodeList = document.getElementsByName("gender")`  
라디오 버튼 목록 Node를 모두 가져오기.

`genderNodeList.forEach(...)`  
가져온 Node 목록을 순회하면서  
Node(라디오 버튼)의 checked 값이 true 인지 확인한다.  
(선택된 라디오 버튼의 checked 값은 true)  
checked 값이 true인 경우, 해당 Node(라디오 버튼)의 value 값을 출력해 준다.
