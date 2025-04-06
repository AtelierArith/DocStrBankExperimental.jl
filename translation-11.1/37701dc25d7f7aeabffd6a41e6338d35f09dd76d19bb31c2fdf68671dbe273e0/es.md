```
Threads.atomic_nand!(x::Atomic{T}, val::T) where T
```

Realiza un nand (no-y) a nivel atómico de `x` con `val`

Realiza `x[] = ~(x[] & val)` de manera atómica. Devuelve el valor **antiguo**.

Para más detalles, consulta la instrucción `atomicrmw nand` de LLVM.

# Ejemplos

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_nand!(x, 2)
3

julia> x[]
-3
```
