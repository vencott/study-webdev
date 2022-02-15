# 12 App - 파일을 이용해 본문 구현

- 본문 내용을 data/ 폴더에 query id 파일명으로 생성한다
- fs.readFile()을 이용해 query id에 따른 본문 내용을 불러온다

```
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
    response.end(template);
  });
```
