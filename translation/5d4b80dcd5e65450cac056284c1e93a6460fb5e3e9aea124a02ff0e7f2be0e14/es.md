```
Threads.atomic_max!(x::Atomic{T}, val::T) where T
```

Almacena de manera atómica el máximo de `x` y `val` en `x`

Realiza `x[] = max(x[], val)` de manera atómica. Devuelve el valor **antiguo**.

Para más detalles, consulta la instrucción `atomicrmw max` de LLVM.

# Ejemplos

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_max!(x, 7)
5

julia> x[]
7
```
