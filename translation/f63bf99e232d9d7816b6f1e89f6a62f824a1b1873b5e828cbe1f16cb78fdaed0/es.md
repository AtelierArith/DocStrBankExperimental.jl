```
trymkpidlock([f::Function], at::String, [pid::Cint]; kwopts...)
trymkpidlock(at::String, proc::Process; kwopts...)
```

Como `mkpidlock` excepto que devuelve `false` en lugar de esperar si el archivo ya está bloqueado.

!!! compat "Julia 1.10"
    Esta función requiere al menos Julia 1.10.

