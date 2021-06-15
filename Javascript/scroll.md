## Scroll
- window.scrollY: 문서가 수직으로 얼마나 스크롤됐는지 (px)
- document.documentElement.clientHeight: 화면의 길이
- document.documentElement.scrollHeight: 총 길이

## Infinite Scroll
- scroll end
```
if(window.scrollY + document.documentElement.clientHeight = document.documentElement.scrollHeight)
```
    