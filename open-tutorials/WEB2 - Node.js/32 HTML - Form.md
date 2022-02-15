# 32 HTML - Form

```
<form action="http://localhost:3000/process_create">
  <p><input type="text" name="title" /></p>
  <p><textarea name="description"></textarea></p>
  <p><input type="submit" /></p>
</form>

// http://localhost:3000/process_create?title=aa&description=aa
```

- submit 버튼을 누르면 action 속성에 기입된 서버에 각 항목의 name과 값으로 된 query string의 형태로 데이터를 전송
- 하지만 이렇게 url로 보내는 것은 절대 하면 안되는 방법이다
- form태그의 method 속성을 POST로 해주면 url에서 가려지게 된다

  `<form action="http://localhost:3000/process_create" method="POST">`
