# 39 App - 글삭제 - 삭제버튼 구현

- 삭제 기능을 구현한다
- delete 버튼을 클릭했을때 a 태그를 통해 어떤 링크로 보내는 것이 아닌 update와 비슷하게 form으로 한다

```
if (queryData.id) {
        var title = queryData.id;
        var list = templateList(files);
        var control = `
        <a href="/update?id=${title}">update</a>
        <form action="/delete_process" method="POST">
        <input type="hidden" name="id" value="${title}">
        <input type="submit" value="delete"/>
        </form>
        `;
        fs.readFile(`data/${title}`, "utf-8", function(err, description) {
          var template = `<h2>${title}</h2><p>${description}</p>`;
          response.writeHead(200);
          response.end(templateHTML(title, list, template, control));
        });
```
