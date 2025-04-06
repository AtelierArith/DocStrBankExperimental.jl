```
redirect_stdout(f::Function, stream)
```

Führen Sie die Funktion `f` aus, während [`stdout`](@ref) an `stream` umgeleitet wird. Nach Abschluss wird [`stdout`](@ref) auf seine vorherige Einstellung zurückgesetzt.
