# 36 App - 글수정 - 수정 링크 생성

## Update

- update 기능은 특정 글이 선택되었을 때만 보여진다
- 수정하고자 하는 파일의 정보를 query string으로 전달한다

```
function templateHTML(title, list, description, control) {
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
    <h2>${title}</h2>
    <p>${description}</p>
  </body>
  </html>
  `;
}

  if (pathname === "/") {
    fs.readdir("./data/", function(err, files) {
      if (queryData.id) {
        var title = queryData.id;
        var list = templateList(files);
        var control = `<a href="/update?id=${title}">update</a>`; // update UI
        fs.readFile(`data/${title}`, "utf-8", function(err, description) {
          response.writeHead(200);
          response.end(templateHTML(title, list, description, control); // need update
        });
      } else {
        var title = "Welcome";
        var list = templateList(files);
        var description = "Hello Node.js";
        response.writeHead(200);
        response.end(templateHTML(title, list, description)); // no update
      }
    });
  }
```
