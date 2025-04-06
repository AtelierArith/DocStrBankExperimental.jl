```
errormonitor(t::Task)
```

Druckt ein Fehlerprotokoll auf `stderr`, wenn die Aufgabe `t` fehlschlägt.

# Beispiele

```julia-repl
julia> Base._wait(errormonitor(Threads.@spawn error("Aufgabe fehlgeschlagen")))
Unhandled Task ERROR: Aufgabe fehlgeschlagen
Stacktrace:
[...]
```
