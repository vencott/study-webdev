# fetch API

## fetch 사용법

```
<input type="button" value="fetch" onclick="
fetch('a').then(function(response) {
    response.text().then(function(text) {
    alert(text);
  })
})
">
```

- a라는 파일을 불러온 뒤 궁극적으로 text라는 곳에 데이터가 담기고 이를 경고창으로 표시

## fetch의 작동원리
- 비동기 함수를 인자로 넘겨준다
- 이를 통해 컴퓨터는 다른 일을 할 수 있다

```
// Asynchronous
function callback() {
    console.log('done');
}

fetch('javascript') // 웹브라우저에게 javascript라는 파일을 서버에게 요청해줘
.then(callback) 	// 서버의 응답이 끝나면 callback이라는 함수를 실행시켜줘

console.log(1);		// 그동안은 다른코드 실행
console.log(2);		// 그동안은 다른코드 실행

// 출력 : 1 2 done
```

## response 객체
- 콜백함수는 익명 함수를 이용하는 것이 좋다
- 콜백함수의 첫번째 인자에 response객체를 넘겨준다

```
fetch('a').then(function(response) {
    if (response.status === 404) {
        alert('Not Found');
        return;
    }
    console.log(response.status)
});
```