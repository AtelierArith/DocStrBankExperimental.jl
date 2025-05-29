```
Add{D} <: AbstractAdd{D}
Add(blocks::AbstractBlock...) -> Add
```

ブロック加算の型。

```jldoctest; setup=:(using Yao)
julia> X + X
nqubits: 1
+
├─ X
└─ X
```
