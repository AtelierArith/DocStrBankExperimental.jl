```
igate(n::Int; nlevel=2)
```

The constructor for [`IdentityGate`](@ref). Let $I_d$ be a $d \times d$ identity matrix, `igate(n; nlevel=d)` is defined as $I_d^{\otimes n}$.

### Examples

```jldoctest; setup=:(using Yao)
julia> igate(2)
igate(2)

julia> igate(2; nlevel=3)
igate(2;nlevel=3)
```
