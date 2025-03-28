```
windowserror(sysfunc[, code::UInt32=Libc.GetLastError()])
windowserror(sysfunc, iftrue::Bool)
```

Wie [`systemerror`](@ref), aber für Windows-API-Funktionen, die [`GetLastError`](@ref Base.Libc.GetLastError) verwenden, um einen Fehlercode zurückzugeben, anstatt [`errno`](@ref Base.Libc.errno) zu setzen.
