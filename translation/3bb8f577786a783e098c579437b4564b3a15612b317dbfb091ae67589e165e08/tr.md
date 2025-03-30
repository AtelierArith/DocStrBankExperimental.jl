```
windowserror(sysfunc[, code::UInt32=Libc.GetLastError()])
windowserror(sysfunc, iftrue::Bool)
```

[`systemerror`](@ref) ile benzer, ancak [`errno`](@ref Base.Libc.errno) ayarlamak yerine bir hata kodu döndürmek için [`GetLastError`](@ref Base.Libc.GetLastError) kullanan Windows API işlevleri için.
