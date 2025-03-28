```
rem(x::Integer, T::Type{<:Integer}) -> T
mod(x::Integer, T::Type{<:Integer}) -> T
%(x::Integer, T::Type{<:Integer}) -> T
```

Trouvez `y::T` tel que `x` ≡ `y` (mod n), où n est le nombre d'entiers représentables dans `T`, et `y` est un entier dans `[typemin(T),typemax(T)]`. Si `T` peut représenter n'importe quel entier (par exemple, `T == BigInt`), alors cette opération correspond à une conversion en `T`.

# Exemples

```jldoctest
julia> x = 129 % Int8
-127

julia> typeof(x)
Int8

julia> x = 129 % BigInt
129

julia> typeof(x)
BigInt
```
