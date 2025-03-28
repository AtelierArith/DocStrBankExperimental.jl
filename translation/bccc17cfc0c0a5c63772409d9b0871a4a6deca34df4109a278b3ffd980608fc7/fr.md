```
Symbol(x...) -> Symbol
```

Créez un [`Symbol`](@ref) en concaténant les représentations sous forme de chaîne des arguments.

# Exemples

```jldoctest
julia> Symbol("my", "name")
:myname

julia> Symbol("day", 4)
:day4
```
