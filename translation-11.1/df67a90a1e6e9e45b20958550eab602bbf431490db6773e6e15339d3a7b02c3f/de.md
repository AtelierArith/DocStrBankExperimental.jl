```
redirect_stderr(f::Function, stream)
```

Führen Sie die Funktion `f` aus, während Sie [`stderr`](@ref) an `stream` umleiten. Nach Abschluss wird [`stderr`](@ref) auf seine vorherige Einstellung zurückgesetzt.
