```
trymkpidlock([f::Function], at::String, [pid::Cint]; kwopts...)
trymkpidlock(at::String, proc::Process; kwopts...)
```

Wie `mkpidlock`, außer dass es `false` zurückgibt, anstatt zu warten, wenn die Datei bereits gesperrt ist.

!!! compat "Julia 1.10"
    Diese Funktion erfordert mindestens Julia 1.10.

