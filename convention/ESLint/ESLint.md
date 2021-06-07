### 설치
```shell
npm i -D eslint
```

.eslintrc.js 생성
```javascript
module.exports = {}
```

```shell
npx eslint app.js
```

### Rules
rules에 [규칙](https://eslint.org/docs/rules/) 추가
```javascript
module.exports = {
    rules: {
        "no-unexpected-multiline": "error",
        "no-extra-semi": "error"
    }
}
```

```shell
# potentially fixable `--fix`로 자동 수정
npx eslint app.js --fix
```

### extends(Extensible Config)
```shell
module.exports = {
  extends: [
    "eslint:recommended",
  ],
}
```
많이 사용하는 extends
- [eslint-config-airbnb-base](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb-base)  
- [eslint-config-standard](https://github.com/standard/eslint-config-standard)

```shell
# --init을 통한 설정
npx eslint --init
```




[출처: 김정환님 블로그](https://jeonghwan-kim.github.io/series/2019/12/30/frontend-dev-env-lint.html#24-%EC%9E%90%EB%8F%99%EC%9C%BC%EB%A1%9C-%EC%88%98%EC%A0%95%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EA%B7%9C%EC%B9%99)
