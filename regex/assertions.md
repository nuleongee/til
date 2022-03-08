### assertions
- (?=\<patter>): \<patter>까지 포함해서 검색하나 \<patter>은 선택에서 제외

---

###### /\w+(?=X)/
`AAA`X---aaax---111
###### /\w+(?=X)/g
`AAA`X---aaax---111

---

###### /\w+/
`AAAX`---aaax---111
###### /\w+/g
`AAAX`---`aaax`---`111`

---

###### /\w+(?=\w)/
`AAA`X---aaax---111
###### /\w+(?=\w)/g
`AAA`X---`aaa`x---`11`1
