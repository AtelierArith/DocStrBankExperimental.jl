```
remotecall_wait(f, id::Integer, args...; kwargs...)
```

Belirtilen `Worker` üzerinde `id` işçi kimliği ile tek bir mesajda daha hızlı bir `wait(remotecall(...))` gerçekleştirin. Anahtar kelime argümanları, varsa, `f`'ye iletilir.

Ayrıca bkz. [`wait`](@ref) ve [`remotecall`](@ref).
