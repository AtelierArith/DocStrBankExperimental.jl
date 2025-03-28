```
Threads.atomic_xchg!(x::Atomic{T}, newval::T) where T
```

Échange atomiquement la valeur dans `x`

Échange atomiquement la valeur dans `x` avec `newval`. Renvoie la **ancienne** valeur.

Pour plus de détails, voir l'instruction `atomicrmw xchg` de LLVM.

# Exemples

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_xchg!(x, 2)
3

julia> x[]
2
```
