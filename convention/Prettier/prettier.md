### 설치
```shell
npm i -D prettier
```

```shell
# --write 옵션으로 파일 재작성
npx prettier app.js --write
```
ESLint와 다르게 규칙이 미리 세팅돼 있어 설정없이 바로 사용 가능


### [ESLint와 Prettier의 통합](https://prettier.io/docs/en/integrating-with-linters.html)
- Prettier: 포매팅
- ESLint: 코드 품질 검사

[eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) : 미리 세팅돼 있는 프리티어 규칙과 충돌하는 ESLint 규칙을 끔
```shell
npm i -D eslint-config-prettier
```
```javascript
//  .eslintrc.js
module.exports = {
  extends: [
    "eslint:recommended",
    "eslint-config-prettier"
  ]
}
```

[eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier) : 프리티어의 모든 규칙을 ESLint로 가져오는 설정
```shell
npm i -D eslint-plugin-prettier
```
```javascript
// .eslintrc.js
module.exports = {
    plugins: [
        "prettier"
    ],
    rules: {
        "prettier/prettier": "error"
    },
}
```

또다른 설정법
```javascript
// .eslintrc.js
module.exports = {
    extends: [
        "eslint:recommended",
        "plugin:prettier/recommended"
    ]
}
```

[출처: 김정환님 블로그](https://jeonghwan-kim.github.io/series/2019/12/30/frontend-dev-env-lint.html#24-%EC%9E%90%EB%8F%99%EC%9C%BC%EB%A1%9C-%EC%88%98%EC%A0%95%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EA%B7%9C%EC%B9%99)
