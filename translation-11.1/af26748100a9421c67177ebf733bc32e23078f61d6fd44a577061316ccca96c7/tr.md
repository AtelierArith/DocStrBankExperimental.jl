```
getindex(tür[, elemanlar...])
```

Belirtilen türde 1-d dizisi oluşturur. Bu genellikle `Tür[]` sözdizimi ile çağrılır. Eleman değerleri `Tür[a,b,c,...]` kullanılarak belirtilebilir.

# Örnekler

```jldoctest
julia> Int8[1, 2, 3]
3-element Vector{Int8}:
 1
 2
 3

julia> getindex(Int8, 1, 2, 3)
3-element Vector{Int8}:
 1
 2
 3
```
