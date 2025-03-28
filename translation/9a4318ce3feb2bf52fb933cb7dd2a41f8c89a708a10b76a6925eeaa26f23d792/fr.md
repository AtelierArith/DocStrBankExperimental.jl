```
real(T::Type)
```

Renvoie le type qui représente la partie réelle d'une valeur de type `T`. Par exemple : pour `T == Complex{R}`, renvoie `R`. Équivalent à `typeof(real(zero(T)))`.

# Exemples

```jldoctest
julia> real(Complex{Int})
Int64

julia> real(Float64)
Float64
```
