# table 가로, 세로 셀 병합하기 colspan, rowspan

## 세로 셀 병합하기 (rowspan)

```html
<table border="1">
  <tr>
    <th>학년</th>
    <th>반</th>
  </tr>
  <tr>
    <td rowspan="2">1</td>
    <td>1</td>
  </tr>
  <tr>
    <!--<td>1</td>-->
    <td>2</td>
  </tr>
  <tr>
    <td>2</td>
    <td>1</td>
  </tr>
</table>
```

| 학년 | 반  |
| ---- | --- |
| `1`  | 1   |
| `1`  | 2   |
| 2    | 1   |

1학년 2개의 셀(row)이 병합됨,  
세로 방향으로 셀이 합쳐졌다.

여러 줄의 row를 병합할 때는  
병합을 시작하려는 cell에 rowspan을 정의하고,  
병합할 row의 개수를 적어준다.

그리고, 원래 해당 cell이 있어야 할 위치 (예제 코드에서 주석으로 처리한 부분)는 비워둔다.

## 가로 셀 병합하기 (colspan)

```html
<table border="1">
  <tr>
    <th>학년</th>
    <th>반</th>
  </tr>
  <tr>
    <td>1</td>
    <td>1</td>
  </tr>
  <tr>
    <td>1</td>
    <td>2</td>
  </tr>
  <tr>
    <td colspan="2">2-1</td>
    <!--<td>1</td>-->
  </tr>
</table>
```

| 학년 | 반  |
| ---- | --- |
| 1    | 1   |
| 1    | 2   |
| `2 ` | `1` |

2개의 column을 병합.  
rkfh 방향으로 셀이 합쳐졌다.

병합하려는 cell에 'colspan' 속성을 정의하고, 병합할 cell의 개수를 지정해한다.

rowspan을 사용할 때와 마찬가지로  
병합된 셀의 위치는 `<td>` 태그를 넣지 않고 비워둔다. (주석 처리된 부분)
