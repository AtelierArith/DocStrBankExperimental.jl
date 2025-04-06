```
systemerror(sysfunc[, errno::Cint=Libc.errno()])
systemerror(sysfunc, iftrue::Bool)
```

`iftrue` `true` ise `sysfunc` ile `errno` için bir `SystemError` oluşturur.
