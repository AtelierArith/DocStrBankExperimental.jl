```
igate(n::Int; nlevel=2)
```

[`IdentityGate`](@ref) のコンストラクタ。$I_d$ を $d \times d$ の単位行列とすると、`igate(n; nlevel=d)` は $I_d^{\otimes n}$ と定義される。

### 例

```jldoctest; setup=:(using Yao)
julia> igate(2)
igate(2)

julia> igate(2; nlevel=3)
igate(2;nlevel=3)
```
