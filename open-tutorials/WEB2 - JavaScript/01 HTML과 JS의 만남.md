# HTML과 JS의 만남

## script 태그

```
<body>
<script>
    document.write('hello world');
</script>
</body>
```

## 이벤트

```
<input type="button" value="버튼" onclick="alert('hi')">
<input type="text" onChange="alert('changed')">
```

- HTML의 onClick 속성의 값으로 JS 코드를 쓴다
- onClick 같은 속성의 속성값은 웹브라우저가 기억하고 있다가 onClick 속성이 속해있는 태그 내에서 실행한다
- onClick, onChange와 같은 속성을 이벤트라고 한다

## 콘솔
- 웹브라우저 오른쪽 클릭 후 검사 선택
- 콘솔에서 JS 코드를 입력해서 실행
- 현재 떠있는 창의 JS 코드처럼 동작한다