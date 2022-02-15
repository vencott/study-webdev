# 02 Node.js - 설치

## Node.js 설치

- https://nodejs.org 접속 후 설치
- 설치가 정상적으로 됐는지를 확인하기 위해 터미널에 다음을 입력한다

`node -v`

- node.js를 시작하기 위해서는 `node`를 입력하고, 나갈때는 ctrl + c 를 두번 연타한다

```
> node
> console.log(1+1);
2
undefined
>
(To exit, press ^C again or type .exit)
>
```

## 파일로 만들어 실행하기

- nodejs라는 새로운 폴더를 만들고, 에디터로 open한다
- helloworld.js 파일을 만든 후, console.log(1+1);을 작성한다
- 터미널에서 nodejs 폴더로 이동해 `node helloworld.js` 를 입력한다

```
> node helloworld.js
2
```
