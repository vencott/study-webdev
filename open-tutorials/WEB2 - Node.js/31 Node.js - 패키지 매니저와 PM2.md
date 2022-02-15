# 31 Node.js - 패키지 매니저와 PM2

## npm

- Node.js의 가장 널리 쓰이는 패키지 매니저
- npm을 통해 다양한 패키지들을 다운받고, 관리할 수 있다

## pm2

- 실행중인 Node.js 애플리케이션을 관리하는 프로세스 매니저

### 설치

`npm install pm2 -g`

### 사용

- 일반적인 실행
  `pm2 start main.js`

- 코드 변경시 자동으로 재실행
  `pm2 start main.js --watch`
