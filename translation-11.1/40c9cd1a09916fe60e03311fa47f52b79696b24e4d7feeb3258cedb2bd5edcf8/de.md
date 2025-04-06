```
remotecall_wait(f, id::Integer, args...; kwargs...)
```

Führen Sie ein schnelleres `wait(remotecall(...))` in einer Nachricht auf dem `Worker` aus, der durch die Worker-ID `id` angegeben ist. Schlüsselwortargumente, falls vorhanden, werden an `f` weitergegeben.

Siehe auch [`wait`](@ref) und [`remotecall`](@ref). ```
