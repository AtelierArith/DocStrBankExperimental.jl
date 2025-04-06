```
hasfield(T::Type, name::Symbol)
```

Renvoie un booléen indiquant si `T` a `name` comme l'un de ses propres champs.

Voir aussi [`fieldnames`](@ref), [`fieldcount`](@ref), [`hasproperty`](@ref).

!!! compat "Julia 1.2"
    Cette fonction nécessite au moins Julia 1.2.


# Exemples

```jldoctest
julia> struct Foo
            bar::Int
       end

julia> hasfield(Foo, :bar)
true

julia> hasfield(Foo, :x)
false
```
