```
global
```

`global x` fait en sorte que `x` dans la portée actuelle et ses portées intérieures se réfère à la variable globale de ce nom. Voir la [section du manuel sur la portée des variables](@ref scope-of-variables) pour plus d'informations.

# Exemples

```jldoctest
julia> z = 3
3

julia> function foo()
           global z = 6 # utilise la variable z définie en dehors de foo
       end
foo (generic function with 1 method)

julia> foo()
6

julia> z
6
```
