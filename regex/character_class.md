### character classes
- \w: word (alphanumeric + "_")
- \W: not word
- \d: digit
- \D: not digit
- \b: word-boundary
- \B: not word-boundary
- \A: beginning of string (multiline 무시) ^과 유사
- \Z: end of string (multiline 무시) $와 유사

---

###### /\w/
`A`1 B2 c3 d_4 e:5 ffGG77--__--
###### /\w/g
`A1` `B2` `c3` `d_4` `e`:`5` `ffGG77`--`__`--

---

###### /\w*/
`A1` B2 c3 d_4 e:5 ffGG77--__--
###### /\w*/g
`A1` `B2` `c3` `d_4` `e`:`5` `ffGG77`--`__`--

---

###### /[a-z]\w*/
A1 B2 `c3` d_4 e:5 ffGG77--__--
###### /[a-z]\w*/g
A1 B2 `c3` `d_4` `e`:5 `ffGG77`--__--

---

###### /\w{5}*/
A1 B2 c3 d_4 e:5 `ffGG7`7--__--
###### /\w{5}/g
A1 B2 c3 d_4 e:5 `ffGG7`7--__--

---

###### /[A-z0-9_]/ === /\w/
`A`1 B2 c3 d_4 e:5 ffGG77--__--
###### /[A-z0-9_]/g === /\w/g
`A1` `B2` `c3` `d_4` `e`:`5` `ffGG77`--`__`--

---

###### /\W/
AS` `_34:As11.23 @#$%12^*
###### /\W/g
AS` `_34`:`As11`.`23` @#$%`12`^*`

---

###### /\w/
`A`S _34:As11.23 @#$%12^*
###### /\w/g
`AS` `_34`:`As11`.`23` @#$%`12`^*

---

###### /[^A-z0-9_]/
AS` `_34:As11.23 @#$%12^*
###### /[^A-z0-9_]/g
AS` `_34`:`As11.23` @#$%`12^`*`

---

###### /\d/
Page `1`23; published: 1234 id=12#24@112
###### /\d/g
Page `123`; published: `1234` id=`12`#`24`@`112`

---

###### /\D/
`P`age 123; published: 1234 id=12#24@112
###### /\D/g
`Page `123`; published: `1234` id=`12`#`24`@`112

---

###### /[0-9]/ === /\d/
Page `1`23; published: 1234 id=12#24@112
###### /[0-9]/g === /\d/g
Page `123`; published: `1234` id=`12`#`24`@`112`

---

###### /[0-9]/ === /\d/
Page `1`23; published: 1234 id=12#24@112
###### /[0-9]/g === /\d/g
Page `123`; published: `1234` id=`12`#`24`@`112`

---

###### /\b\w/g
`E`re `i`ron `w`as `f`ound `o`r `t`ree `a` `w`as `h`ewn, `W`hen `y`oung `w`as `m`ountain `u`nder `m`oon;

###### /\w\b/g
Er`e` iro`n` wa`s` foun`d` o`r` tre`e` `a` wa`s` hew`n`, Whe`n` youn`g` wa`s` mountai`n` unde`r` moo`n`;

###### /\b\w+\b/g
`Ere` `iron` `was` `found` `or` `tree` `a` `was` `hewn`, `When` `young` `was` `mountain` `under` `moon`;

###### /\bcat/g
`cat` concat

###### /cat\b/g
`cat` con`cat`

---

###### /\B./g
c`a``t` c`o``n``c``a``t`

###### /\B.\B/g
c`a`t c`o``n``c``a`t

---

###### /\A.../
`Ere` iron was found or tree a was hewn, When young was mountain under moon;
###### /\A.../g
`Ere` iron was found or tree a was hewn, When young was mountain under moon;

###### /\Z.../
Ere iron was found or tree a was hewn, When young was mountain under mo`on;`
###### /\Z.../g
Ere iron was found or tree a was hewn, When young was mountain under mo`on;`
