# 34 App - POST 방식으로 전송된 데이터 받기

- 사용자가 POST 방식으로 전송한 데이터를 Node.js에선 어떻게 처리해야 할까
- 우선 /create_process 페이지를 컨트롤하는 분기를 넣는다

`else if (pathname === "/create_process") {}`

## Extract Post Data in Node.js

```
var qs = require("querystring");

// ...

else if (pathname === "/create_process") {
    var body = "";

    request.on("data", function(data) {
      body += data;
    });

    request.on("end", function() {
      var post = qs.parse(body);
      console.log(post);
    });
  }
```

### request.on("data", func(data){})

- data의 크기가 너무 클 경우 프로그램에 부담이 될 수 있다
- 그래서 서버에서 데이터의 조각 조각을 받을 때마다 콜백 함수로 이 데이터(수신한 정보)를 넘겨준다
- 더이상 수신할 데이터가 없으면 'end'를 호출하도록 약속되어 있다

### request.on("end", func(){})

- 정보 수신이 끝났을 때 호출된다
- 콘솔에 찍어보면 다음과 같이 출력된다

`{ title: 'zz', description: 'zz' }`

- 이를 통해 POST를 통해 받은 데이터가 객체화 된것을 확인할 수 있다
