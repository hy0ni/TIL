# 체크박스에 체크된 항목 개수 구하기

```html
<input type="checkbox" name="animal" value="dog" onclick="getCheckedCnt()" /> 개
<input type="checkbox" name="animal" value="cat" onclick="getCheckedCnt()" /> 고양이
<input type="checkbox" name="animal" value="rabbit" onclick="getCheckedCnt()" /> 토끼
<div id="result"></div>
```

```javascript
function getCheckedCnt() {
  // 선택된 목록 가져오기
  const query = 'input[name="animal"]:checked';
  const selectedElements = document.querySelectorAll(query);

  // 선택된 목록의 개수 세기
  const selectedElementsCount = selectedElements.length;

  // 출력
  document.getElementById("result").innerText = selectedElementsCount;
}
```

**`선택된 목록 가져오기`**  
document.querySelectorAll(query) 함수를 사용하여 선택된 전체 체크박스 element를 찾기.  
document 전체에서 query 조건에 맞는 모든 element를 찾아
NodeList 형태로 리턴.

**`선택된 목록의 개수 세기`**  
체크박스에 체크된 항목의 개수를 구하기 위해
'selectedElements' 변수에 담긴 목록의 길이(length)를 구함.
