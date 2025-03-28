```
windowserror(sysfunc[, code::UInt32=Libc.GetLastError()])
windowserror(sysfunc, iftrue::Bool)
```

Como [`systemerror`](@ref), pero para funciones de la API de Windows que utilizan [`GetLastError`](@ref Base.Libc.GetLastError) para devolver un código de error en lugar de establecer [`errno`](@ref Base.Libc.errno).
