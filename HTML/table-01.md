# 기본 테이블(표, Table) 그리기

HTML에서 웹페이지에 Table(표)을 표현하기 위해서 주로 `<table>` 태그를 사용한다.

```html
<table border="1">
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

`<tr>`  
tr은 'table row'의 약자로, 테이블의 행을 표현한다.

`<td>`  
td는 'table data'의 약자이다.  
td 태그는 테이블에 들어가는 데이터, 셀을 의미한다.

하나의 테이블 안에 `<tr>` 태그로 행을 표현하고,  
그 안에 `<td>` 태그를 이용하여 데이터를 표현 한다.

`<th>`  
th는 'table header'의 약자로 테이블의 타이틀을 표현한다.

`<td>와 <th> 차이점`

`<td>`

- 보통 굵기 글씨
- 왼쪽 정렬(left-aligned)

`<th>`

- 굵은 글씨(bold)
- 가운데 정렬(center)
