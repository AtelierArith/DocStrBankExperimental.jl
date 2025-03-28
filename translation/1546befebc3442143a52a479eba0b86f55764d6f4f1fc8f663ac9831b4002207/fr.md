```
Threads.atomic_xor!(x::Atomic{T}, val::T) where T
```

Effectue un xor (ou exclusif) au niveau des bits de manière atomique entre `x` et `val`.

Effectue `x[] $= val` de manière atomique. Renvoie la **ancienne** valeur.

Pour plus de détails, voir l'instruction `atomicrmw xor` de LLVM.

# Exemples

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_xor!(x, 7)
5

julia> x[]
2
```
