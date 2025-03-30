```
issparse(S)
```

`S` seyrekse `true`, değilse `false` döner.

# Örnekler

```jldoctest
julia> sv = sparsevec([1, 4], [2.3, 2.2], 10)
10-elemanlı SparseVector{Float64, Int64} ile 2 saklanan girdi:
  [1]  =  2.3
  [4]  =  2.2

julia> issparse(sv)
true

julia> issparse(Array(sv))
false
```
