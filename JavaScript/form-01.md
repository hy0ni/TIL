# input type='file' 속성 알아보기

```html
<form>
  <input
    type="file"
    accept="image/*,.txt"
    multiple
    required
    capture="user"
    onchange="aaa"
  />
  <input type="submit" />
</form>
```

## accept

입력받을 수 있는 파일의 유형을 지정하는 속성.
accept 속성을 지정하지 않으면 모든 유형의 파일을 입력 받을 수 있다.
여러 종류의 파일을 입력받기 위해서는 쉼표로 목록을 구분하여 작성한다.

**`accept 속성 값`**

- 확장자 명( .txt, .pdf 등 처럼 마침표로 시작하는 확장자 명을 써준다.)
- MIME 타입 ex) text/plain, image/jpeg, audio/mpeg, image/\* 등

'모든 파일(_._)'을 선택할 경우,
지정된 이미지 파일과 텍스트 파일 이외의 파일도 입력 받을 수 있습니다.

## capture

모바일 디바이스에 적용되는 속성.
accept 속성에 이미지 또는 비디오를 입력받는 경우, 기기의 어떤 카메라를 이용할지 지정한다.

**`capture 속성 값`**

- user : 전면 카메라
- environment : 후면 카메라

## files

사용자가 파일을 선택하면, 선택된 파일의 목록이 FileList 객체 형태로 files 속성에 저장된다.
즉, 선택된 파일 목록을 가져오려면 files 속성을 참조하면 된다.

## multiple

사용자가 ctrl / shift 키를 사용하여 한번에 여러개의 파일을 선택하게 할지, 한번에 하나의 파일만 선택하게 할지를 결정하는 속성.
boolean 값을 가진다.

## required

form이 submit 될때, 반드시 파일이 선택되어야 하는지 여부를 지정하는 속성.
'required' 속성이 지정되었는데, 파일을 선택하지 않고, submit 하게 되면,
파일을 선택하라는 메세지가 나온다.
boolean 값을 가진다.

## value

사용자가 선택한 파일의 경로 값을 가진다.
만약, 여러 파일을 선택한 경우, 목록의 첫번째 파일 경로 값만을 가진다.
단, 악의적인 사용을 방지하기 위해 모든 파일의 경로 앞에 'C:\fakepath\'가 포함된다.
