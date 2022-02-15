# CSS 선택자

## 클래스 선택자
- 그루핑을 위한 문법
- 선택자의 앞에 .을 써서 특정 클래스를 선택하게 할 수 있다
- 클래스 속성에는 여러개의 값이 들어올 수 있고 띄어쓰기로 구분한다
- 하나의 태그에는 여러개의 속성이 들어올 수 있고 여러개의 선택자를 통해서 하나의 태그를 공동으로 제어할 수 있다

```
<style>
    a {
        color: black;
        text-decoration: none;
    }
    .saw {
        color: gray;
    }
    .active {
        color: red;
    }
    h1 {
        font-size: 45px;
        text-align: center;
    }
</style>

<li><a href="intro.html" class="saw">소개</a></li> // gray
<li><a href="member.html" class="saw active">멤버</a></li> // red
<li><a href="movie.html">동영상</a></li> // black
```

- active 선택자가 마지막에 위치하기 때문에 빨간색이 된 것이다
- 이는 그다지 좋은 방법이 아니다

## id 선택자
- 선택자에 앞에 #을 써서 특정 id를 선택하게 할 수 있다
- 클래스 선택자보다 우선순위가 높다
- 선택자 우선순위 : id > 클래스 > 태그
- id 속성은 단 한번만 등장한다(유일무이)
- 태그가 id보다 더 포괄적이고, id가 더 구체적이다
- CSS를 설계할 때 구체적인 것을 포괄적인 것보다 우선순위를 높게 설정하였다

```
<style>
    a {
        color: black;
        text-decoration: none;
    }
    #active {
        color: red;
    }
    .saw {
        color: gray;
    }
    h1 {
        font-size: 45px;
        text-align: center;
    }
</style>

<li><a href="intro.html" class="saw">소개</a></li> // gray
<li><a href="member.html" class="saw" id="active">멤버</a></li> // red
<li><a href="movie.html">동영상</a></li> // black
```