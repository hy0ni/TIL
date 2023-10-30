# 로컬 텍스트 파일 읽기 (다중 파일 선택)

HTML/Javascrip로 로컬 텍스트 파일을 읽어서
선택한 파일에 대한 정보 (파일명, 파일크기 등)을 보여주는 방법.

Ctrl / Shift 키를 사용하여 여러개의 파일을 선택할 수 있다.

```html
<form>
  <div>
    <input type="file" id="fileUploads" accept=".txt" multiple />
  </div>
  <div class="preview">
    <p></p>
  </div>
</form>
```

input의 type 속성을 file로 지정하면 파일을 입력 받을 수 있다.
accept 속성을 지정하여, 입력받는 파일의 종류를 지정할 수 있음.

multiple 속성을 지정하면, ctrl/shift 키를 사용하여 다수의 파일을 선택할 수 있다.

```javascript
const $input = document.querySelector("input");
const $preview = document.querySelector(".preview");

$input.addEventListener("change", showTextFile);

function showTextFile() {
  const selectedFiles = $input.files;
  const list = document.createElement("ul");
  $preview.appendChild(list);

  for (const file of selectedFiles) {
    const listItem = document.createElement("li");

    if (validFileType(file)) {
      const summary = document.createElement("div");
      summary.textContent = `파일명 : ${
        file.name
      }, 파일 크기 : ${returnFileSize(file.size)}.`;
      const textContents = document.createElement("div");

      let reader = new FileReader();
      reader.onload = function () {
        textContents.innerText = reader.result;
      };
      reader.readAsText(file, "UTF-8");

      listItem.appendChild(summary);
      listItem.appendChild(textContents);
    } else {
      const message = document.createElement("div");
      message.textContent = `파일명 ${file.name}: .txt 파일을 선택하세요`;
      listItem.appendChild(message);
    }

    list.appendChild(listItem);
  }
}

const fileTypes = ["text/plain"];

function validFileType(file) {
  return fileTypes.includes(file.type);
}

function returnFileSize(number) {
  if (number < 1024) {
    return number + "bytes";
  } else if (number > 1024 && number < 1048576) {
    return (number / 1024).toFixed(1) + "KB";
  } else if (number > 1048576) {
    return (number / 1048576).toFixed(1) + "MB";
  }
}
```

```javascript
$input.addEventListener("change", showTextFile);
```

input에 'change' 이벤트가 발생(파일 선택)되면 showTextFile 함수를 실행한다.

```javascript
const selectedFiles = $input.files;
```

파일이 선택되면 input의 'files' property에 'FileList'형태로 선택된 파일 정보가 저장된다.
'FileList'는 선택된 'File'의 list 형태이다.

```javascript
for (const file of selectedFiles)
```

선택된 파일 목록에서 파일을 하나씩 꺼내온다.

```javascript
if(validFileType(file)) {

const fileTypes = [
   'text/plain',
];

function validFileType(file) {
  return fileTypes.includes(file.type);
}
```

'File' 객체는 'type'속성을 가지고 있다.
선택된 파일이 'text/plain' 타입인지 확인함.
물론, HTML의 accept 속성을 통해서 '.txt' 파일을 선택하도록 했지만, 이 속성은 강제성이 없다.

사용자가 원한다면 다른 속성의 파일을 선택 할 수 있기 때문에 파일을 입력받은 후, 파일의 type을 체크한다.

```javascript
summary.textContent = `파일명 : ${file.name}, 파일 크기 : ${returnFileSize(
  file.size
)}.`;

function returnFileSize(number) {
  if (number < 1024) {
    return number + "bytes";
  } else if (number > 1024 && number < 1048576) {
    return (number / 1024).toFixed(1) + "KB";
  } else if (number > 1048576) {
    return (number / 1048576).toFixed(1) + "MB";
  }
}
```

'File'객체는 name, size속성을 가지고 있다. (file.name, file.size)
이 속성을 사용하여 파일명과 파일크기를 가져온다.
file.size는 byte단위의 파일사이즈를 리턴.
returnFileSize 함수로 byte단위를 byte, kb, mb로 변환한다.

```javascript
let reader = new FileReader();
reader.onload = function () {
  textContents.innerText = reader.result;
};
reader.readAsText(file, "UTF-8");
```

'FileReader' 객체는 파일을 읽을 수 있도록 도와주는 객체다.
FileReader 객체의 'readAsText' 메서드를 사용하여 파일의 텍스트를 읽는다.

readAsText를 호출할 경우, 읽어들인 파일의 내용은 FileReader 객체의 'result' 속성에 저장된다.

파일이 성공적으로 읽혀지면, FileReader 객체의 onload 이벤트가 발생한다.

이때 FileReader객체의 result속성에 저장된 text파일의 내용을 화면에 뿌려준다.
