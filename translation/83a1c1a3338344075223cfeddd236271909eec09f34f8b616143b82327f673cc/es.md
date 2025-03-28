```
Threads.atomic_and!(x::Atomic{T}, val::T) where T
```

Realiza una operación atómica de AND a nivel de bits entre `x` y `val`

Realiza `x[] &= val` de manera atómica. Devuelve el valor **antiguo**.

Para más detalles, consulta la instrucción `atomicrmw and` de LLVM.

# Ejemplos

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_and!(x, 2)
3

julia> x[]
2
```
