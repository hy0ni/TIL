> 조건문

## switch 문

switch 문은 하나의 변수나 표현식을 여러 값과 비교하여 해당하는 값의 코드 블록을 실행합니다. 동일한 변수의 여러 값에 따라 실행할 코드를 분기할 때 유용합니다.

```javascript
// 구문
switch (expression) {
  case value1:
    // value1이 expression과 일치할 때 실행되는 코드
    break;
  case value2:
    // value2가 expression과 일치할 때 실행되는 코드
    break;
  // 필요한 만큼 case 추가
  default:
  // 모든 case가 일치하지 않을 때 실행되는 코드
}
```

- expression은 비교할 변수나 표현식입니다.
- case value:는 expression이 value와 일치할 때 실행할 코드 블록을 정의합니다.
- break;는 코드 블록이 끝난 후 switch 문을 빠져나오게 합니다. break를 사용하지 않으면 다음 case로 넘어가서 계속 실행됩니다(이것을 "fall-through"라고 합니다).
- default(생략가능):는 어떤 case도 일치하지 않을 때 실행할 코드 블록을 정의합니다.

```javascript
let grade = "B";

switch (grade) {
  case "A":
    console.log("우수한 성적입니다.");
    break;
  case "B":
    console.log("좋은 성적입니다.");
    break;
  case "C":
    console.log("괜찮은 성적입니다.");
    break;
  case "D":
    console.log("노력이 필요합니다.");
    break;
  default:
    console.log("재시험이 필요합니다.");
    break;
}
// result: 좋은 성적입니다.
```

1. let grade = "B";: grade 변수를 "B"로 설정합니다.
2. switch (grade): grade 변수의 값을 검사합니다.
3. case "A":부터 case "D":까지 각각의 case는 grade가 해당 값과 일치할 때 실행됩니다.
4. 각 case 블록 끝에 break 문을 사용하여 해당 case 블록이 끝난 후 switch 문을 빠져나갑니다.
5. default: 블록은 grade 값이 어떤 case와도 일치하지 않을 때 실행됩니다.

- break 문을 사용하지 않으면 다음 case 블록이 실행되므로 잊지 말고 추가해야 합니다. 다만, 의도적으로 "fall-through"를 사용할 경우에는 break를 생략할 수 있습니다.
- default 블록은 선택 사항이지만, 어떤 case도 일치하지 않을 때 실행될 코드를 정의할 때 유용합니다.

\*\* fall-through는 switch 문에서 case 블록에 break 문이 없을 때 다음 case로 넘어가 계속 실행되는 현상을 말합니다. 즉, 일치하는 case를 찾은 후 break 없이 다음 case 블록까지 실행되는 것을 의미합니다.

## if문과 switch문의 차이점

`if문`은 복잡한 조건을 검사하거나, 서로 다른 조건을 비교할 때 사용합니다.

`switch문`은 하나의 변수에 대해 여러값을 비교할 때, 값이 명확하게 나뉠 때(ex. 메뉴 선택, 특정 명령어 처리)사용합니다.

1. 조건 검사 방식

- if 문은 논리 조건을 사용하여 true/false를 검사합니다.
- switch 문은 하나의 변수나 표현식을 여러 값과 비교합니다.

2. 복잡성

- if 문은 복잡한 논리와 다양한 조건을 처리할 수 있습니다.
- switch 문은 단순히 값에 따라 분기하는 경우 더 읽기 쉽고 간결합니다.

3. 가독성

- if 문은 조건이 많아질수록 코드가 길어지고 복잡해질 수 있습니다.
- switch 문은 여러 값에 대해 분기할 때 코드가 더 명확하고 가독성이 좋습니다.

여러 조건을 논리적으로 비교해야 할 때는 if문,  
하나의 변수에 대해 여러 고정된 값을 비교할 때는 switch문을 사용합니다.
