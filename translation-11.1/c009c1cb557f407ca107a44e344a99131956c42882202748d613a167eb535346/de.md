```
Integer <: Real
```

Abstrakte Oberklasse für alle Ganzzahlen (z. B. [`Signed`](@ref), [`Unsigned`](@ref) und [`Bool`](@ref)).

Siehe auch [`isinteger`](@ref), [`trunc`](@ref), [`div`](@ref).

# Beispiele

```
julia> 42 isa Integer
true

julia> 1.0 isa Integer
false

julia> isinteger(1.0)
true
```
