```
Threads.atomic_sub!(x::Atomic{T}, val::T) where T <: ArithmeticTypes
```

Soustrait atomiquement `val` de `x`

Effectue `x[] -= val` de manière atomique. Renvoie la **ancienne** valeur. Non défini pour `Atomic{Bool}`.

Pour plus de détails, voir l'instruction `atomicrmw sub` de LLVM.

# Exemples

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_sub!(x, 2)
3

julia> x[]
1
```
