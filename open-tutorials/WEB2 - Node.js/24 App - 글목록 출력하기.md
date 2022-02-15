# 24 App - 글목록 출력하기

- data 디렉토리에 있는 파일들의 이름을 이용해서 글 목록을 생성
- fs.readdir()을 통해 파일 이름으로 list를 생성해서 보여준다

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

  if (pathname === "/") {
    if (queryData.id === undefined) {
      fs.readdir("./data/", function(err, files) {
        var title = "Welcome";
        var description = "Hello Node.js";
        var list = "<ul>";
        files.forEach(file => {
          list += `<li><a href="/?id=${file}">${file}</a></li>`;
        });
        list += "</ul>";

        var template = `
      <!doctype html>
    <html>
    <head>
      <title>WEB1 - ${title}</title>
      <meta charset="utf-8">
    </head>
    <body>
      <h1><a href="/">WEB</a></h1>
      ${list}
      <h2>${title}</h2>
      <p>${description}</p>
    </body>
    </html>
      `;
        response.writeHead(200);
        response.end(template);
      });
    } else {
      fs.readdir("./data/", function(err, files) {
        var title = queryData.id;
        var list = "<ul>";
        files.forEach(file => {
          list += `<li><a href="/?id=${file}">${file}</a></li>`;
        });
        list += "</ul>";

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
      ${list}
      <h2>${title}</h2>
      <p>${description}</p>
    </body>
    </html>
    `;
          response.writeHead(200);
          response.end(template);
        });
      });
    }
  } else {
    response.writeHead(404);
    response.end("Not found");
  }
});
app.listen(3000);
```
