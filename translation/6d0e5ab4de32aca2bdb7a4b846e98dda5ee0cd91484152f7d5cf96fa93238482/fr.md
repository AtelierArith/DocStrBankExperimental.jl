```
systemerror(sysfunc[, errno::Cint=Libc.errno()])
systemerror(sysfunc, iftrue::Bool)
```

Lève une `SystemError` pour `errno` avec la chaîne descriptive `sysfunc` si `iftrue` est `true`
