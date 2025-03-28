```
findnext(pattern::AbstractString, string::AbstractString, start::Integer)
findnext(pattern::AbstractPattern, string::String, start::Integer)
```

Trouver la prochaine occurrence de `pattern` dans `string` en commençant à la position `start`. `pattern` peut être soit une chaîne de caractères, soit une expression régulière, auquel cas `string` doit être de type `String`.

La valeur de retour est une plage d'indices où la séquence correspondante est trouvée, de sorte que `s[findnext(x, s, i)] == x` :

`findnext("substring", string, i)` == `start:stop` tel que `string[start:stop] == "substring"` et `i <= start`, ou `nothing` si aucune correspondance n'est trouvée.

# Exemples

```jldoctest
julia> findnext("z", "Hello to the world", 1) === nothing
true

julia> findnext("o", "Hello to the world", 6)
8:8

julia> findnext("Lang", "JuliaLang", 2)
6:9
```
