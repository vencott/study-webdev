# fetch API polyfill
- web은 한 기업이 만드는 기술이 아니라 공공재
- 그러므로 어떤 기능이 있을때 그 기능을 모든 브라우저가 지원하지 않을 수 있다
- 이런 과거의 브라우저를 사용하는 사용자들도 그 기능을 쓸 수 있게 해주는 것을 polyfill이라 한다

## fetch의 polyfill
- fetch를 다운받은 다음 다음 문장을 추가한다

```
<script src="lib/fetch/fetch.js"></script>
```

- 지원되는 브라우저에서는 활성화되지 않고, 지원되지 않는 브라우저에서만 fetch.js가 동작한다