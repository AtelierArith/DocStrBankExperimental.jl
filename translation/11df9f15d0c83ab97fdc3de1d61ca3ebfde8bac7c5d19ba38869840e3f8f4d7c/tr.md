```
NTuple{N, T}
```

`N` uzunluğunda ve tüm elemanları `T` tipinde olan bir demetin tipini temsil etmenin kompakt bir yolu.

# Örnekler

```jldoctest
julia> isa((1, 2, 3, 4, 5, 6), NTuple{6, Int})
true
```

Ayrıca bkz. [`ntuple`](@ref).
