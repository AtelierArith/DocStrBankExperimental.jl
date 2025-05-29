```
relax!(register[, locs]; to_nactive=nqudits(register)) -> register
relax!(locs::Int...; to_nactive=nqudits(register)) -> f(register) -> register
```

[`focus!`](@ref) の逆変換であり、`to_nactive` はターゲットレジスタのアクティブビットの数です。レジスタが提供されていない場合、レジスタを入力として受け取るラムダ関数を返します。

### 例

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"01101")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 5/5
    nlevel: 2

julia> focus!(reg, (1,3,4))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/5
    nlevel: 2

julia> relax!(reg, (1,3,4))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 5/5
    nlevel: 2
```
