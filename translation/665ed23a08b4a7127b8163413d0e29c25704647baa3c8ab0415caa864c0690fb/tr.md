```
merge!(d::AbstractDict, others::AbstractDict...)
```

Diğer koleksiyonlardan çiftlerle koleksiyonu güncelle. Ayrıca bkz. [`merge`](@ref).

# Örnekler

```jldoctest
julia> d1 = Dict(1 => 2, 3 => 4);

julia> d2 = Dict(1 => 4, 4 => 5);

julia> merge!(d1, d2);

julia> d1
Dict{Int64, Int64} with 3 entries:
  4 => 5
  3 => 4
  1 => 4
```
