```
redirect_stdin(f::Function, stream)
```

Führen Sie die Funktion `f` aus, während [`stdin`](@ref) auf `stream` umgeleitet wird. Nach Abschluss wird [`stdin`](@ref) auf seine vorherige Einstellung zurückgesetzt.
