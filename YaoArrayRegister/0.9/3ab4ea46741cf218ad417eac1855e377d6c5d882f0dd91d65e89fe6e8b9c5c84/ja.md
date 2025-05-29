```julia
most_probable(
    reg::YaoArrayRegister.ArrayReg{D, T} where T,
    n::Int64
) -> Any

```

量子レジスタ内の `n` 個の最も確率の高いキュービット構成を見つけ、これらの構成を `DitStr` インスタンスのベクターとして返します。

### 例

```jldoctest; setup=:(using Yao)
julia> most_probable(ghz_state(3), 2)
2-element Vector{DitStr{2, 3, Int64}}:
 000 ₍₂₎
 111 ₍₂₎
```
