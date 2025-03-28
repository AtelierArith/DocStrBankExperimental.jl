```
isconcretetype(T)
```

Bestimmen Sie, ob der Typ `T` ein konkreter Typ ist, was bedeutet, dass er direkte Instanzen haben könnte (Werte `x`, sodass `typeof(x) === T`). Beachten Sie, dass dies nicht die Negation von `isabstracttype(T)` ist. Wenn `T` kein Typ ist, geben Sie `false` zurück.

Siehe auch: [`isbits`](@ref), [`isabstracttype`](@ref), [`issingletontype`](@ref).

# Beispiele

```jldoctest
julia> isconcretetype(Complex)
false

julia> isconcretetype(Complex{Float32})
true

julia> isconcretetype(Vector{Complex})
true

julia> isconcretetype(Vector{Complex{Float32}})
true

julia> isconcretetype(Union{})
false

julia> isconcretetype(Union{Int,String})
false
```
