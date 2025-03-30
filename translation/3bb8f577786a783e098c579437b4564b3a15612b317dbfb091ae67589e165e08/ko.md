```
windowserror(sysfunc[, code::UInt32=Libc.GetLastError()])
windowserror(sysfunc, iftrue::Bool)
```

[`systemerror`](@ref)와 유사하지만, [`errno`](@ref Base.Libc.errno)를 설정하는 대신 오류 코드를 반환하기 위해 [`GetLastError`](@ref Base.Libc.GetLastError)를 사용하는 Windows API 함수에 대한 것입니다.
