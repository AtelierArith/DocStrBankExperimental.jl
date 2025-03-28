```
stacktrace([trace::Vector{Ptr{Cvoid}},] [c_funcs::Bool=false]) -> StackTrace
```

Gibt einen Stack-Trace in Form eines Vektors von `StackFrame`s zurück. (Standardmäßig gibt `stacktrace` keine C-Funktionen zurück, aber dies kann aktiviert werden.) Wenn `stacktrace` ohne Angabe eines Traces aufgerufen wird, ruft es zuerst `backtrace` auf.
