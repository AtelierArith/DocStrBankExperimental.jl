```
parameters_eltype(x)
```

[`parameters`](@ref) の要素型を返します。

### 例

```jldoctest; setup=:(using Yao)
julia> parameters_eltype(chain(Rx(0.1), Rz(0.1f0)))
Float64
```
