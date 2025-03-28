```
string(n::Integer; base::Integer = 10, pad::Integer = 1)
```

Convertir un entier `n` en une chaîne dans la base donnée, en spécifiant éventuellement un nombre de chiffres à compléter.

Voir aussi [`digits`](@ref), [`bitstring`](@ref), [`count_zeros`](@ref).

# Exemples

```jldoctest
julia> string(5, base = 13, pad = 4)
"0005"

julia> string(-13, base = 5, pad = 4)
"-0023"
```
