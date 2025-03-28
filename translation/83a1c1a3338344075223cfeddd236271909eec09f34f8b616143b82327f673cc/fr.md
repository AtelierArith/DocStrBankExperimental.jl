```
Threads.atomic_and!(x::Atomic{T}, val::T) where T
```

Effectue un ET bit à bit atomique de `x` avec `val`

Effectue `x[] &= val` de manière atomique. Renvoie la **ancienne** valeur.

Pour plus de détails, voir l'instruction `atomicrmw and` de LLVM.

# Exemples

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_and!(x, 2)
3

julia> x[]
2
```
