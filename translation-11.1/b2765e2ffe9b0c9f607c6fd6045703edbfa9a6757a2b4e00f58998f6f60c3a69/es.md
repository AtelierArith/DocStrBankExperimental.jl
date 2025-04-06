```
Threads.atomic_xchg!(x::Atomic{T}, newval::T) where T
```

Intercambia atómicamente el valor en `x`

Intercambia atómicamente el valor en `x` con `newval`. Devuelve el valor **antiguo**.

Para más detalles, consulta la instrucción `atomicrmw xchg` de LLVM.

# Ejemplos

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_xchg!(x, 2)
3

julia> x[]
2
```
