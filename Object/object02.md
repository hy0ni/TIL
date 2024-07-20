> Object(객체)

## "this" 는 무엇인가?

```javascript
let person = {
  name: "Bob",
  greeting: function () {
    console.log(`Hi I'm ${this.name}`);
  },
};
person.greeting();
```

this 키워드는 지금 동작하고 있는 코드를 가지고 있는 객체를 가리킵니다.  
위에 예제에서 this는 person객체와 동일합니다.  
this는 객체 멤버의 컨텍스트가 바뀌는 경우에도 언제나 정확한 값을 사용하게 해줍니다.

\*\*객체 멤버의 컨텍스트(Context)는 그 멤버가 실행될 때 this 키워드가 참조하는 객체를 의미합니다. 즉, 컨텍스트는 함수나 메서드가 호출되는 환경을 나타내며, 이 환경에 따라 this의 값이 결정됩니다.

```javascript
let person = {
  name: "Bob",
  greeting: function () {
    console.log(`Hi I'm ${this.name}`);
  },
};
person.greeting(); // Hi I'm Bob
```

위 예제를 보면  
person.greeting()은 Hi I'm Bob을 출력합니다.  
this는 실행중인 코드가 속해있는 객체입니다.  
객체 리터럴을 직접 지정해서 사용하는 경우라면 그리 유용하지 않겠지만, 동적으로 객체를 생성하는 경우(ex.생성자를 사용하는 경우)에는 매우 유용합니다.   
