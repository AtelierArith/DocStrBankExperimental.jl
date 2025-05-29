```
circled(str)
```

文字列 `str` の円で囲まれた/ボックスされた文字をUnicodeテーブルから返します。

```
A-Z           "A" -> "Ⓐ"  Ⓐ:Ⓩ       
a-z           "a" -> "ⓐ"  ⓐ:ⓩ       
0-9           "0" -> "⓪"  ①:⑨       
A-Z inverse   "A" -> "🅐"  🅐:🅩     
a-z inverse   "a" -> "🅰"  🅰:🆉     
```
