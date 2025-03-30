```
GitShortHash(hash::GitHash, len::Integer)
```

一个缩短的 git 对象标识符，当它是唯一时可以用来识别一个 git 对象，由 `hash` 的前 `len` 个十六进制数字组成（其余数字被忽略）。
