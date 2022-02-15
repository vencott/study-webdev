# 04 Node.js - 웹서버 만들기

- Node.js는 웹서버 기능을 가지고 있다
- main.js를 다음과 같이 작성한 후 실행시켜본다

```
// main.js
var http = require("http");
var fs = require("fs");
var app = http.createServer(function(request, response) {
  var url = request.url;
  if (request.url == "/") {
    url = "/index.html";
  }
  if (request.url == "/favicon.ico") {
    response.writeHead(404);
    response.end();
    return;
  }
  response.writeHead(200);
  console.log(__dirname + url);
  response.end(fs.readFileSync(__dirname + url));
});
app.listen(3000);
```

```
// terminal
> node main.js
/Users/jungminkim/Development/private/groupnokdu/index.html
/Users/jungminkim/Development/private/groupnokdu/1.html
/Users/jungminkim/Development/private/groupnokdu/coding.jpg
/Users/jungminkim/Development/private/groupnokdu/2.html
/Users/jungminkim/Development/private/groupnokdu/3.html
```
