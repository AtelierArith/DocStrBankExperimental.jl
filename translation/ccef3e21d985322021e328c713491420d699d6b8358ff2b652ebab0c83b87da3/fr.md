```
Threads.atomic_min!(x::Atomic{T}, val::T) where T
```

Stocke de manière atomique le minimum de `x` et `val` dans `x`

Effectue `x[] = min(x[], val)` de manière atomique. Renvoie la **ancienne** valeur.

Pour plus de détails, voir l'instruction `atomicrmw min` de LLVM.

# Exemples

```jldoctest
julia> x = Threads.Atomic{Int}(7)
Base.Threads.Atomic{Int64}(7)

julia> Threads.atomic_min!(x, 5)
7

julia> x[]
5
```
