```
NaN, NaN64
```

Une valeur not-a-number de type [`Float64`](@ref).

Voir aussi : [`isnan`](@ref), [`missing`](@ref), [`NaN32`](@ref), [`Inf`](@ref).

# Exemples

```jldoctest
julia> 0/0
NaN

julia> Inf - Inf
NaN

julia> NaN == NaN, isequal(NaN, NaN), isnan(NaN)
(false, true, true)
```

!!! note
    Utilisez toujours [`isnan`](@ref) ou [`isequal`](@ref) pour vérifier la présence de `NaN`. Utiliser `x === NaN` peut donner des résultats inattendus :

    ```julia-repl
    julia> reinterpret(UInt32, NaN32)
    0x7fc00000

    julia> NaN32p1 = reinterpret(Float32, 0x7fc00001)
    NaN32

    julia> NaN32p1 === NaN32, isequal(NaN32p1, NaN32), isnan(NaN32p1)
    (false, true, true)
    ```

