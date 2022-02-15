# 11 Node.js - 파일 읽기

## CRUD

- Create, Read, Update, Delete
- 정보를 다루는 핵심적인 처리 방법

## fs

- node.js에서 파일 읽기는 fs.readFile()을 이용한다

```
// fileread.js
const fs = require("fs");

fs.readFile("sample.txt", "utf8", function(err, data) {
  console.log(data);
});
```
