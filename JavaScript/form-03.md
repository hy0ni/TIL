# 디렉토리 선택하여 파일 리스트 가져오기 (이름, 상대경로)

사용자가 디렉토리 선택 시, 디렉토리(폴더) 안의 파일을 목록을 읽어오는 방법.

## webkitdirectory

사용자가 파일이 아닌 디렉토리를 선택하게 하기 위해서는
input 태그의 속성으로 'webkitdirectory' 속성을 지정해 준다.

```html
<input type="file" webkitdirectory />
```

webkitdirectory 속성을 지정하면 사용자는 파일이 아닌 디렉토리를 선택할 수 있게 된다.  
( 단, 이 속성은 chrome 및 microsoft edge 등 대부분의 많은 브라우저들에서 작동하지만, 표준은 아니기 때문에 Internet Explorer에서는 작동하지 않음. )

## 디렉토리 안의 파일 정보 읽어오기

'webkitdirectory' 속성을 적용하여
디렉토리를 선택하고,
선택한 디렉토리 안의 파일의 상대 경로와 파일명 목록 가져오기.

```html
<form>
  <div>
    <input type="file" id="directory_upload" webkitdirectory />
  </div>
  <div class="file_list">
    <p></p>
  </div>
</form>
```

HTML 파일에서 사용자가 디렉토리를 선택할 수 있도록 input 속성에 webkitdirctory 속성을 지정한다.

```javascript
const $input = document.querySelector("input");
const $preview = document.querySelector(".file-list");

$input.addEventListener("change", showTextFile);

function showTextFile() {
  const selectedFiles = $input.files;
  const list = document.createElement("ul");
  $preview.appendChild(list);

  for (const file of selectedFiles) {
    const listItem = document.createElement("li");
    const summary = document.createElement("div");

    summary.textContent = file.webkitRelativePath;

    listItem.appendChild(summary);
    list.appendChild(listItem);
  }
}
```

## 디렉토리 안의 파일 상대경로 가져오기

```javascript
file.webkitRelativePath;
```

file 객체의 webkitRelativePath 속성을 이용하여,
디렉토리 안의 파일의 상대 경로를 가져올 수 있다.

## 디렉토리 안의 파일명 가져오기

```javascript
// summary.textContent = file.webkitRelativePath;
summary.textContent = file.name;
```

webkitRelativePath 속성이 아닌 file.name으로 변경하면
상대 경로를 제외한 파일의 이름만 가져올 수 있다.
