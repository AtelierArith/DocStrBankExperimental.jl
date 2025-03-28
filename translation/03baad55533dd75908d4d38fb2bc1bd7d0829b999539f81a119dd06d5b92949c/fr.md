```
eps(::Type{T}) where T<:AbstractFloat
eps()
```

Renvoie le *epsilon machine* du type à virgule flottante `T` (`T = Float64` par défaut). Cela est défini comme l'écart entre 1 et la valeur suivante la plus grande représentable par `typeof(one(T))`, et est équivalent à `eps(one(T))`.  (Puisque `eps(T)` est une limite sur l'*erreur relative* de `T`, c'est une quantité "sans dimension" comme [`one`](@ref).)

# Exemples

```jldoctest
julia> eps()
2.220446049250313e-16

julia> eps(Float32)
1.1920929f-7

julia> 1.0 + eps()
1.0000000000000002

julia> 1.0 + eps()/2
1.0
```
