```
systemerror(sysfunc[, errno::Cint=Libc.errno()])
systemerror(sysfunc, iftrue::Bool)
```

Lanza un `SystemError` para `errno` con la cadena descriptiva `sysfunc` si `iftrue` es `true`
