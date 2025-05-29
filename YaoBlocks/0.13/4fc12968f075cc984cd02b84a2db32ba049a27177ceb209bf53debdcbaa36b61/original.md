```
Add{D} <: AbstractAdd{D}
Add(blocks::AbstractBlock...) -> Add
```

Type for block addition.

```jldoctest; setup=:(using Yao)
julia> X + X
nqubits: 1
+
├─ X
└─ X
```
