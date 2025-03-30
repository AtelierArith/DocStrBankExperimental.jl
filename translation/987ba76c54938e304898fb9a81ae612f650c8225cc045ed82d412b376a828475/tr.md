```
errormonitor(t::Task)
```

Görev `t` başarısız olursa `stderr`'ye bir hata günlüğü yazdırır.

# Örnekler

```julia-repl
julia> Base._wait(errormonitor(Threads.@spawn error("görev başarısız oldu")))
Unhandled Task ERROR: görev başarısız oldu
Stacktrace:
[...]
```
