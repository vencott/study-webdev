# 30 Node.js - 동기와 비동기 그리고 콜백

## synchronous & asynchronous

- synchronous : 동기적, 직관적이나 효율적이지 않다
- asynchronous : 비동기적, 효율적이나 복잡하다
- Node.js는 비동기적인 처리를 위한 다양한 방법들을 제공한다

```
var fs = require('fs');

/*
// readFileSync - 동기
console.log('A');
var result = fs.readFileSync('syntax/sample.txt', 'utf8');
console.log(result);
console.log('C');

// result: A B C
*/

// readFile - 비동기
console.log('A');
fs.readFile('syntax/sample.txt', 'utf8', function(err, result){
    console.log(result);
});
console.log('C');

// result: A C B
```

## callback

```
var a = function(){
  console.log('A');
}


function slowfunc(callback){
  callback();
}

slowfunc(a);
```
