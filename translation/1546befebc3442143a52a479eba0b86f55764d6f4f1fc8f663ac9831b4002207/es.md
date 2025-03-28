```
Threads.atomic_xor!(x::Atomic{T}, val::T) where T
```

Realiza una operación atómica de xor a nivel de bits (o exclusivo) entre `x` y `val`.

Realiza `x[] $= val` de manera atómica. Devuelve el valor **antiguo**.

Para más detalles, consulta la instrucción `atomicrmw xor` de LLVM.

# Ejemplos

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_xor!(x, 7)
5

julia> x[]
2
```
