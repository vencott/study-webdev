# 18 App - Not found 오류 구현

## Url 분석

`console.log(url.parse(_url, true));`

```
Url {
  protocol: null,
  slashes: null,
  auth: null,
  host: null,
  port: null,
  hostname: null,
  hash: null,
  search: null,
  query: {},
  pathname: '/',
  path: '/',
  href: '/' }
```

## 예외 처리하기

- pathname이 '/'인 경우만 정상 접근으로 처리하고, 나머지는 404 오류 메시지를 출력한다

```
// modules
var http = require("http");
var fs = require("fs");
var url = require("url");

// app
var app = http.createServer(function(request, response) {
  var _url = request.url;
  var queryData = url.parse(_url, true).query;
  var pathname = url.parse(_url, true).pathname;
  var title = queryData.id;

  if (pathname === "/") {
    fs.readFile(`data/${title}`, "utf-8", function(err, description) {
      var template = `
    <!doctype html>
  <html>
  <head>
    <title>WEB1 - ${title}</title>
    <meta charset="utf-8">
  </head>
  <body>
    <h1><a href="/">WEB</a></h1>
    <ol>
      <li><a href="/?id=HTML">HTML</a></li>
      <li><a href="/?id=CSS">CSS</a></li>
      <li><a href="/?id=JavaScript">JavaScript</a></li>
    </ol>
    <h2>${title}</h2>
    <p>${description}</p>
  </body>
  </html>
    `;
      response.writeHead(200);
      response.end(template);
    });
  } else {
    response.writeHead(404);
    response.end("Not found");
  }
});
app.listen(3000);

```
