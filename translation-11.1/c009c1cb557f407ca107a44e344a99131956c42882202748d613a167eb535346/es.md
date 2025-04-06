```
Integer <: Real
```

Supertipo abstracto para todos los enteros (por ejemplo, [`Signed`](@ref), [`Unsigned`](@ref) y [`Bool`](@ref)).

Véase también [`isinteger`](@ref), [`trunc`](@ref), [`div`](@ref).

# Ejemplos

```
julia> 42 isa Integer
true

julia> 1.0 isa Integer
false

julia> isinteger(1.0)
true
```
