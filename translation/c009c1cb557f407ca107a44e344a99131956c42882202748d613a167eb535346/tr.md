```
Tam sayı <: Gerçek
```

Tüm tam sayılar için soyut üst tür (örneğin, [`Signed`](@ref), [`Unsigned`](@ref) ve [`Bool`](@ref)).

Ayrıca bkz. [`isinteger`](@ref), [`trunc`](@ref), [`div`](@ref).

# Örnekler

```
julia> 42 isa Integer
true

julia> 1.0 isa Integer
false

julia> isinteger(1.0)
true
```
