```
windowserror(sysfunc[, code::UInt32=Libc.GetLastError()])
windowserror(sysfunc, iftrue::Bool)
```

类似于 [`systemerror`](@ref)，但用于 Windows API 函数，这些函数使用 [`GetLastError`](@ref Base.Libc.GetLastError) 返回错误代码，而不是设置 [`errno`](@ref Base.Libc.errno)。
