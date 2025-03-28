```
systemerror(sysfunc[, errno::Cint=Libc.errno()])
systemerror(sysfunc, iftrue::Bool)
```

Löst einen `SystemError` für `errno` mit der beschreibenden Zeichenkette `sysfunc` aus, wenn `iftrue` `true` ist.
