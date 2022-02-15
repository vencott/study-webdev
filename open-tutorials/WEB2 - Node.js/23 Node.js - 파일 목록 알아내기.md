# 23 Node.js - 파일 목록 알아내기

## fs.readdir()

```
// nodejs/readdir.js
var target = "./data/"; // 이 파일을 기준으로 하는것이 아니라 nodejs를 실행시킨 root를 기준으로 path를 작성
var fs = require("fs");

fs.readdir(target, function(err, files) {
  console.log(files);
});

// [ 'CSS', 'HTML', 'JavaScript' ]
```
