# 37 App - 글수정 - 수정할 정보 전송

## update

- update_process 로 수정한 내용을 form 형식으로 전달한다
- 이때 제목이 변경될 수도 있으므로 수정되기 이전의 파일명을 알기 위해 hidden type으로 id 구분자를 넘겨준다

```
// modules
var http = require("http");
var fs = require("fs");
var url = require("url");
var qs = require("querystring");

// functions
function templateHTML(title, list, body, control) {
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
    <a href="/create">create</a> ${control ? control : ""}
    ${body}
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
        var control = `<a href="/update?id=${title}">update</a>`;
        fs.readFile(`data/${title}`, "utf-8", function(err, description) {
          var template = `<h2>${title}</h2><p>${description}</p>`;
          response.writeHead(200);
          response.end(templateHTML(title, list, template, control));
        });
      } else {
        var title = "Welcome";
        var list = templateList(files);
        var description = "Hello Node.js";
        var template = `<h2>${title}</h2><p>${description}</p>`;
        response.writeHead(200);
        response.end(templateHTML(title, list, template));
      }
    });
  } else if (pathname === "/create") {
    fs.readdir("./data/", function(err, files) {
      var title = "WEB - create";
      var list = templateList(files);
      var template = `
      <form action="/create_process" method="POST">
      <p><input type="text" name="title" placeholder="title"/></p>
      <p><textarea name="description" placeholder="description"></textarea></p>
      <p><input type="submit" /></p>
      </form>`;
      response.writeHead(200);
      response.end(templateHTML(title, list, template));
    });
  } else if (pathname === "/create_process") {
    var body = "";

    request.on("data", function(data) {
      body += data;
    });

    request.on("end", function() {
      var post = qs.parse(body);
      var title = post.title;
      var description = post.description;

      fs.writeFile(`data/${title}`, description, "utf8", function(err) {
        response.writeHead(302, { Location: `/?id=${title}` }); // redirection
        response.end();
      });
    });
  } else if (pathname === "/update") {
    fs.readdir("./data/", function(err, files) {
      var title = queryData.id;
      var list = templateList(files);
      var control = `<a href="/update?id=${title}">update</a>`;
      fs.readFile(`data/${title}`, "utf-8", function(err, description) {
        response.writeHead(200);
        response.end(
          templateHTML(
            title,
            list,
            `
        <form action="/update_process" method="POST">
        <input type="hidden" name="id" value="${title}">
        <p><input type="text" name="title" placeholder="title" value="${title}"/></p>
        <p><textarea name="description" placeholder="description">${description}</textarea></p>
        <p><input type="submit" /></p>
        </form>`,
            control
          )
        );
      });
    });
  } else {
    response.writeHead(404);
    response.end("Not found");
  }
});
app.listen(3000);

```
