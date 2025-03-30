```
systemerror(sysfunc[, errno::Cint=Libc.errno()])
systemerror(sysfunc, iftrue::Bool)
```

如果 `iftrue` 为 `true`，则为 `errno` 引发一个 `SystemError`，并使用描述性字符串 `sysfunc`。
