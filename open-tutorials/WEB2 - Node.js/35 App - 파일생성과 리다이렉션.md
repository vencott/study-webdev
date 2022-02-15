# 35 App - 파일생성과 리다이렉션

## 파일 생성

- POST 방식으로 받은 데이터를 data 디렉토리 안에 파일 형식으로 저장해보자

```
else if (pathname === "/create_process") {
    var body = "";

    request.on("data", function(data) {
      body += data;
    });

    request.on("end", function() {
      var post = qs.parse(body);
      var title = post.title;
      var description = post.description;

      fs.writeFile(`data/${title}`, description, "utf8", function(err) {
        response.writeHead(200);
        response.end("success");
      });
    });
  }
```

## 리다이렉션

- 사용자가 create 하면 해당 페이지로 이동

```
fs.writeFile(`data/${title}`, description, "utf8", function(err) {
        response.writeHead(302, { Location: `/?id=${title}` }); // redirection
        response.end();
      });
```
