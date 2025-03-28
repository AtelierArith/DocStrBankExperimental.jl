```
Threads.atomic_or!(x::Atomic{T}, val::T) where T
```

Effectue un ou bit à bit atomique de `x` avec `val`

Effectue `x[] |= val` de manière atomique. Renvoie la **ancienne** valeur.

Pour plus de détails, voir l'instruction `atomicrmw or` de LLVM.

# Exemples

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_or!(x, 7)
5

julia> x[]
7
```
