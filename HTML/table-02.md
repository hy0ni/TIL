# 테이블 제목 지정하기 caption tag

테이블의 제목을 지정하기 위해서 `<caption>`이라는 태그를 사용한다.

```html
<table border="1">
  <caption>
    나라와 수도
  </caption>
  <tr>
    <th>나라</th>
    <th>수도</th>
  </tr>
  <tr>
    <td>한국</td>
    <td>서울</td>
  </tr>
  <tr>
    <td>영국</td>
    <td>런던</td>
  </tr>
</table>
```

`<caption>` 태그는 `<table>` 태그 안에서 사용되며, 테이블의 제목을 표현한다.

아무런 속성을 지정하지 않고 `<caption>` 태그를 사용할 경우,  
테이블의 caption 정보는 테이블의 위쪽에, 가운데 정렬되어 표현된다.

캡션의 위치와 정렬 방법을 지정하기 위해서는 css를 활용함.  
`caption-side`: top|bottom|initial|inherit;  
`text-align`: left|right|center|justify|initial|inherit;
