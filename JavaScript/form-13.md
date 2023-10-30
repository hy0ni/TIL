# 체크박스 중, 하나라도 선택 해제될 경우 전체 선택 해제하기

```html
<input type="checkbox" name="selectAll" value="selectAll" onclick="selectAll(this)" />Select All
<input type="checkbox" name="animal" value="dog" onclick="checkSelectAll()" /> 개
<input type="checkbox" name="animal" value="cat" onclick="checkSelectAll()" /> 고양이
<input type="checkbox" name="animal" value="rabbit" onclick="checkSelectAll()" /> 토끼
```

```javascript
function checkSelectAll() {
  // 전체 체크박스
  const checkboxes = document.querySelectorAll('input[name="animal"]');

  // 선택된 체크박스
  const checked = document.querySelectorAll('input[name="animal"]:checked');

  // selectAll 체크박스
  const selectAll = document.querySelector('input[name="selectAll"]');

  if (checkboxes.length === checked.length) {
    selectAll.checked = true;
  } else {
    selectAll.checked = false;
  }
}

function selectAll(selectAll) {
  const checkboxes = document.getElementsByName("animal");

  checkboxes.forEach((checkbox) => {
    checkbox.checked = selectAll.checked;
  });
}
```

animal 체크박스에 onclick 이벤트가 발생할 때마다 checkSelectAll() 함수를 실행.  
전체 체크박스(checkboxes)와 선택된 체크박스(checked)의 개수를 비교하여  
개수가 같으면 selectAll 체크박스가 선택되도록 하고,  
개수가 같지 않으면 selectAll 체크박스(selectAll)가 선택해제 되도록 구현.
