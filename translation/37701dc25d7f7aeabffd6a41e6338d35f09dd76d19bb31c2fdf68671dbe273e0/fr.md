```
Threads.atomic_nand!(x::Atomic{T}, val::T) où T
```

Effectue un nand (non-et) bit à bit atomique de `x` avec `val`

Effectue `x[] = ~(x[] & val)` de manière atomique. Renvoie la **ancienne** valeur.

Pour plus de détails, voir l'instruction `atomicrmw nand` de LLVM.

# Exemples

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_nand!(x, 2)
3

julia> x[]
-3
```
