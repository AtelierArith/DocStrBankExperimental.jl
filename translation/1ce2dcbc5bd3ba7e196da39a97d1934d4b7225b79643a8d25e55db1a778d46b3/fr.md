```
@isdefined s -> Bool
```

Teste si la variable `s` est définie dans le scope actuel.

Voir aussi [`isdefined`](@ref) pour les propriétés de champ et [`isassigned`](@ref) pour les index de tableau ou [`haskey`](@ref) pour d'autres mappages.

# Exemples

```jldoctest
julia> @isdefined newvar
false

julia> newvar = 1
1

julia> @isdefined newvar
true

julia> function f()
           println(@isdefined x)
           x = 3
           println(@isdefined x)
       end
f (generic function with 1 method)

julia> f()
false
true
```
