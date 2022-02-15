# 28 App - 함수를 이용해서 정리 정돈하기

```
// modules
var http = require("http");
var fs = require("fs");
var url = require("url");

// functions
function templateHTML(title, description, list) {
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
      var title = queryData.id ? queryData.id : "Welcome";
      var list = templateList(files);

      if (queryData.id === undefined) {
        var description = "Hello Node.js";
        response.writeHead(200);
        response.end(templateHTML(title, description, list));
      } else {
        fs.readFile(`data/${title}`, "utf-8", function(err, description) {
          response.writeHead(200);
          response.end(templateHTML(title, description, list));
        });
      }
    });
  } else {
    response.writeHead(404);
    response.end("Not found");
  }
});
app.listen(3000);
```
