# 라디오 버튼의 텍스트 클릭하여, 항목 선택하기

## Label 사용하기

```html
<input type="radio" name="gender" value="female" id="female" />
<label for="female">여성</label>

<input type="radio" name="gender" value="male" id="male" />
<label for="male">남성</label>
```

특정 라디오 버튼과 라디오 버튼을 설명하는 텍스트를 연결하기 위해  
label 태그와 'for' 속성 사용.

### label 태그 안에 라디오 버튼을 중첩시켜서 사용하기

```html
<label>
  <input type="radio" name="gender" value="female" id="female" />
  여성
</label>

<label>
  <input type="radio" name="gender" value="male" id="male" />
  남성
</label>
```

label 태그에 'for' 속성을 사용하지 않고  
label 태그 안에 라디오 버튼을 중첩시켜도 동일하게 작동함.
