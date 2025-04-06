```
trymkpidlock([f::Function], at::String, [pid::Cint]; kwopts...)
trymkpidlock(at::String, proc::Process; kwopts...)
```

与 `mkpidlock` 类似，但如果文件已经被锁定，则返回 `false` 而不是等待。

!!! compat "Julia 1.10"
    此函数至少需要 Julia 1.10。

