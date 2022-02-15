# 09 Node.js - URL로 입력된 값 사용하기

## URL의 이해

`http://opentutorials.org:3000/main?id=HTML&page=12`

- http
  - protocol
- opentutorials.org
  - host(domain name)
- 3000
  - port: 3000번 포트와 연결되어있는 서버와 통신
- main
  - path: 어떤 디렉토리의 어떤 파일인지
- id=HTML&page=12
  - query string: ?로 시작하고 원하는 정보를 기입

## Node.js에서 URL을 통해서 입력된 값을 사용하는 방법

```
var url = require("url");
var queryData = url.parse(_url, true).query;
console.log(queryData);
```

- http://localhost:3000/index.html?id=2&name=s 로 입력하면, 다음과 같이 출력된다

`{ id: '2', name: 's' }`
