```
sizeof(str::AbstractString)
```

Taille, en octets, de la chaîne `str`. Égal au nombre d'unités de code dans `str` multiplié par la taille, en octets, d'une unité de code dans `str`.

# Exemples

```jldoctest
julia> sizeof("")
0

julia> sizeof("∀")
3
```
