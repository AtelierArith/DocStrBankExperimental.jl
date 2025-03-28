```
findprev(pattern::AbstractString, string::AbstractString, start::Integer)
```

Trouver la précédente occurrence de `pattern` dans `string` en commençant à la position `start`.

La valeur de retour est une plage d'indices où la séquence correspondante est trouvée, de sorte que `s[findprev(x, s, i)] == x` :

`findprev("substring", string, i)` == `start:stop` tel que `string[start:stop] == "substring"` et `stop <= i`, ou `nothing` si aucune correspondance n'est trouvée.

# Exemples

```jldoctest
julia> findprev("z", "Hello to the world", 18) === nothing
true

julia> findprev("o", "Hello to the world", 18)
15:15

julia> findprev("Julia", "JuliaLang", 6)
1:5
```
