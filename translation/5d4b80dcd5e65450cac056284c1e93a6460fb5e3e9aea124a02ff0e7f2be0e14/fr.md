```
Threads.atomic_max!(x::Atomic{T}, val::T) where T
```

Stocke de manière atomique le maximum de `x` et `val` dans `x`

Effectue `x[] = max(x[], val)` de manière atomique. Renvoie la **ancienne** valeur.

Pour plus de détails, voir l'instruction `atomicrmw max` de LLVM.

# Exemples

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_max!(x, 7)
5

julia> x[]
7
```
