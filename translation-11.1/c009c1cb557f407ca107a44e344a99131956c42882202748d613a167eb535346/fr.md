```
Integer <: Real
```

Supertype abstrait pour tous les entiers (par exemple [`Signed`](@ref), [`Unsigned`](@ref), et [`Bool`](@ref)).

Voir aussi [`isinteger`](@ref), [`trunc`](@ref), [`div`](@ref).

# Exemples

```
julia> 42 isa Integer
true

julia> 1.0 isa Integer
false

julia> isinteger(1.0)
true
```
