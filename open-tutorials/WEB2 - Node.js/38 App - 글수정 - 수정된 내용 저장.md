# 38 App - 글수정 - 수정된 내용 저장

- /update_process에 POST 방식으로 들어온 데이터를 가공해서 저장한다
- 파일명을 먼저 바꾼 후, 파일에 데이터를 쓴다

```
else if (pathname === "/update_process") {
    var body = "";

    request.on("data", function(data) {
      body += data;
    });

    request.on("end", function() {
      var post = qs.parse(body);

      var id = post.id;
      var title = post.title;
      var description = post.description;

      fs.rename(`data/${id}`, `data/${title}`, function(err) {
        fs.writeFile(`data/${title}`, description, "utf8", function(err) {
          response.writeHead(302, { Location: `/?id=${title}` }); // redirection
          response.end();
        });
      });
    });
  }
```
