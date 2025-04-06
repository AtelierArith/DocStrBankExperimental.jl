```
axes(A)
```

Gibt das Tupel der gültigen Indizes für das Array `A` zurück.

Siehe auch: [`size`](@ref), [`keys`](@ref), [`eachindex`](@ref).

# Beispiele

```jldoctest
julia> A = fill(1, (5,6,7));

julia> axes(A)
(Base.OneTo(5), Base.OneTo(6), Base.OneTo(7))
```
