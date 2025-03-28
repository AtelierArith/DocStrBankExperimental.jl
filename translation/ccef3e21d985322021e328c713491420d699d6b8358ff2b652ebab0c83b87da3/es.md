```
Threads.atomic_min!(x::Atomic{T}, val::T) where T
```

Almacena de manera atómica el mínimo de `x` y `val` en `x`

Realiza `x[] = min(x[], val)` de manera atómica. Devuelve el valor **antiguo**.

Para más detalles, consulta la instrucción `atomicrmw min` de LLVM.

# Ejemplos

```jldoctest
julia> x = Threads.Atomic{Int}(7)
Base.Threads.Atomic{Int64}(7)

julia> Threads.atomic_min!(x, 5)
7

julia> x[]
5
```
