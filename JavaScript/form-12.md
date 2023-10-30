# 체크박스 전체 선택 / 전체 해제 구현하기

- [체크박스 전체 선택 / 전체 해제 구현하기](#체크박스-전체-선택--전체-해제-구현하기)
  - [Document.getElementsByName() 활용하기](#documentgetelementsbyname-활용하기)
  - [Document.querySelectorAll() 활용하기](#documentqueryselectorall-활용하기)

## Document.getElementsByName() 활용하기

```html
<input type="checkbox" name="animal" value="selectAll" onclick="selectAll(this)" />
<b>Select All</b>
<br />
<input type="checkbox" name="animal" value="dog" /> 개
<br />
<input type="checkbox" name="animal" value="cat" /> 고양이
<br />
<input type="checkbox" name="animal" value="rabbit" /> 토끼
```

```javascript
function selectAll(selectAll) {
  const checkboxes = document.getElementsByName("animal");

  checkboxes.forEach((checkbox) => {
    checkbox.checked = selectAll.checked;
  });
}
```

`document.getElementsByName("animal");`  
name='animal'인 모든 element를 찾아서 NodeList 형태로 리턴함.

forEach 반복문을 사용하여 순회하면서 각 체크박스의 checked 값을  
'Select All' element의 check 값(selectAll.checked)과 동일하게 변경한다.

'Select All' 체크박스가 선택되면, 나머지 체크박스도 모두 선택되고,  
'Select All' 체크박스가 선택 해제되면, 나머지 체크박스도 모두 선택 해제된다.

## Document.querySelectorAll() 활용하기

```javascript
function selectAll(selectAll) {
  const checkboxes = document.querySelectorAll('input[type="checkbox"]');

  checkboxes.forEach((checkbox) => {
    checkbox.checked = selectAll.checked;
  });
}
```

`document.querySelectorAll('input[type="checkbox"]');`  
input type이 checkbox인 목록을 리턴함.
