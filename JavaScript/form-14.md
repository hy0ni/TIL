# 체크박스 하나만 선택되게 하기

사용자가 여러 개의 항목 중 한 가지만 선택해야 한다면 라디오 버튼을 사용해야 한다.

체크박스는 보통 다중 선택이 필요할 때 많이 사용하는데,  
반드시 체크박스로 구현해야 할 경우 사용할 수 있는 방법이다.

```html
<input type="checkbox" name="animal" value="dog" onclick="checkOnlyOne(this)" /> 개
<input type="checkbox" name="animal" value="cat" onclick="checkOnlyOne(this)" /> 고양이
<input type="checkbox" name="animal" value="rabbit" onclick="checkOnlyOne(this)" /> 토끼
```

```javascript
function checkOnlyOne(element) {
  const checkboxes = document.getElementsByName("animal");

  checkboxes.forEach((el) => {
    el.checked = false;
  });

  element.checked = true;
}
```

각각의 체크박스들은 onclick 이벤트가 발생했을 때  
'checkOnlyOne()' 함수를 호출하고, 파라미터로 this(자기 자신) element를 전달한다.

`document.getElementsByName("animal")`  
document에서 'animal'이라는 이름을 가진 모든 element를 찾아서  
NodeList 형태로 리턴한다.

name='animal'인 3개의 체크박스가 리턴됨.

forEach 반복문으로 앞에서 선택된 모든 체크박스를 순회하며 checked 값을 false로 지정해
체크박스 선택을 해제함.

`element.checked = true`  
파라미터로 전달된 체크박스(클릭된 체크박스)의 checked 값을 true로 변경해서,
해당 체크박스가 선택되도록 함.
