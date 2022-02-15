# 40 App - 글삭제 기능 완성

- /delete_process에서 삭제 기능을 구현한다

```
else if (pathname === "/delete_process") {
    var body = "";

    request.on("data", function(data) {
      body += data;
    });

    request.on("end", function() {
      var post = qs.parse(body);
      var id = post.id;

      fs.unlink(`data/${id}`, function() {
        response.writeHead(302, { Location: `/` }); // redirection
        response.end();
      });
    });
  }
```
