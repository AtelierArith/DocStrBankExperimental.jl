```
insert!(a::Vector, index::Integer, item)
```

Fügen Sie ein `item` in `a` an dem angegebenen `index` ein. `index` ist der Index von `item` im resultierenden `a`.

Siehe auch: [`push!`](@ref), [`replace`](@ref), [`popat!`](@ref), [`splice!`](@ref).

# Beispiele

```jldoctest
julia> insert!(Any[1:6;], 3, "here")
7-element Vector{Any}:
 1
 2
  "here"
 3
 4
 5
 6
```
