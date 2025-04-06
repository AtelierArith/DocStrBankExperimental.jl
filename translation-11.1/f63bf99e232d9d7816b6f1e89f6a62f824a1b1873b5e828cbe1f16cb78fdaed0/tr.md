```
trymkpidlock([f::Function], at::String, [pid::Cint]; kwopts...)
trymkpidlock(at::String, proc::Process; kwopts...)
```

`mkpidlock` gibi, ancak dosya zaten kilitlenmişse beklemek yerine `false` döner.

!!! compat "Julia 1.10"
    Bu fonksiyon en az Julia 1.10 gerektirir.

