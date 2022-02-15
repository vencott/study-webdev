# 33 App - 글생성 UI 만들기

- /create 주소를 만들어서 글 생성 UI를 개발
- pathname이 /create 일 경우에 글 생성 페이지의 내용을 출력한다(Form)

```
// modules
var http = require("http");
var fs = require("fs");
var url = require("url");

// functions
function templateHTML(title, list, description) {
  return `
  <!doctype html>
  <html>
  <head>
    <title>WEB1 - ${title}</title>
    <meta charset="utf-8">
  </head>
  <body>
    <h1><a href="/">WEB</a></h1>
    ${list}
    <a href="/create">create</a>
    <h2>${title}</h2>
    <p>${description}</p>
  </body>
  </html>
  `;
}

function templateList(files) {
  var list = "<ul>";
  files.forEach(file => {
    list += `<li><a href="/?id=${file}">${file}</a></li>`;
  });
  list += "</ul>";
  return list;
}

// app
var app = http.createServer(function(request, response) {
  var _url = request.url;
  var queryData = url.parse(_url, true).query;
  var pathname = url.parse(_url, true).pathname;

  if (pathname === "/") {
    fs.readdir("./data/", function(err, files) {
      if (queryData.id) {
        var title = queryData.id;
        var list = templateList(files);
        fs.readFile(`data/${title}`, "utf-8", function(err, description) {
          response.writeHead(200);
          response.end(templateHTML(title, list, description));
        });
      } else {
        var title = "Welcome";
        var list = templateList(files);
        var description = "Hello Node.js";
        response.writeHead(200);
        response.end(templateHTML(title, list, description));
      }
    });
  } else if (pathname === "/create") {
    fs.readdir("./data/", function(err, files) {
      var title = "WEB - create";
      var list = templateList(files);
      var description = `
      <form action="http://localhost:3000/process_create" method="POST">
      <p><input type="text" name="title" placeholder="title"/></p>
      <p><textarea name="description" placeholder="description"></textarea></p>
      <p><input type="submit" /></p>
      </form>`;
      response.writeHead(200);
      response.end(templateHTML(title, list, description));
    });
  } else {
    response.writeHead(404);
    response.end("Not found");
  }
});
app.listen(3000);
```
