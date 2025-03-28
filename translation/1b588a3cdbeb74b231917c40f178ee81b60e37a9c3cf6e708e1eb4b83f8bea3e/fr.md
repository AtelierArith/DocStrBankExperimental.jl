```
Fonction
```

Type abstrait de toutes les fonctions.

# Exemples

```jldoctest
julia> isa(+, Function)
true

julia> typeof(sin)
typeof(sin) (type singleton de la fonction sin, sous-type de Function)

julia> ans <: Function
true
```
