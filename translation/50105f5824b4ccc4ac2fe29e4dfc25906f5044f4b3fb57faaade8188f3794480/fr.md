```
Dict([itr])
```

`Dict{K,V}()` construit une table de hachage avec des clés de type `K` et des valeurs de type `V`. Les clés sont comparées avec [`isequal`](@ref) et hachées avec [`hash`](@ref).

Étant donné un seul argument itérable, construit un [`Dict`](@ref) dont les paires clé-valeur sont tirées de 2-uplets `(clé,valeur)` générés par l'argument.

# Exemples

```jldoctest
julia> Dict([("A", 1), ("B", 2)])
Dict{String, Int64} avec 2 entrées :
  "B" => 2
  "A" => 1
```

Alternativement, une séquence d'arguments de paires peut être passée.

```jldoctest
julia> Dict("A"=>1, "B"=>2)
Dict{String, Int64} avec 2 entrées :
  "B" => 2
  "A" => 1
```

!!! avertissement
    Les clés peuvent être mutables, mais si vous modifiez des clés stockées, la table de hachage peut devenir inconsistente en interne, auquel cas le `Dict` ne fonctionnera pas correctement. [`IdDict`](@ref) peut être une alternative si vous devez modifier des clés.

