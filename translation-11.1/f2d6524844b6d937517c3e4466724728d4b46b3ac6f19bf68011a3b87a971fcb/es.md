```
Threads.atomic_or!(x::Atomic{T}, val::T) donde T
```

Realiza un OR a nivel de bits de manera atómica entre `x` y `val`

Realiza `x[] |= val` de manera atómica. Devuelve el valor **antiguo**.

Para más detalles, consulta la instrucción `atomicrmw or` de LLVM.

# Ejemplos

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_or!(x, 7)
5

julia> x[]
7
```
