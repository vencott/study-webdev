# CSS 코드의 재사용
- HTML 파일에 직접 style 태그를 추가하는 유지보수와 코드중복의 관점에서 매우 좋지 않다
- 이를 해결하기 위해 css 코드를 파일로 따로 분리한 후 HTML 문서에서 링크 태그를 이용하여 활용한다

```
<head>
    <meta charset="UTF-8">
    <title>녹두그룹</title>
    <link rel="stylesheet" href="css/style.css">
</head>
```