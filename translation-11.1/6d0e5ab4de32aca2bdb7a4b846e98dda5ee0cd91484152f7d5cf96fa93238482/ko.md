```
systemerror(sysfunc[, errno::Cint=Libc.errno()])
systemerror(sysfunc, iftrue::Bool)
```

`iftrue`가 `true`일 경우 `sysfunc`에 대한 설명 문자열과 함께 `errno`에 대해 `SystemError`를 발생시킵니다.
