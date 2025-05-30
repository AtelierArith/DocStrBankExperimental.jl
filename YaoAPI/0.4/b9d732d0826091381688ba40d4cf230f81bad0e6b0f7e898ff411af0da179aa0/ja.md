```
density_matrix(register_or_rho[, locations])
```

指定された`locations`の量子ビットに対する縮退密度行列を返します（デフォルト：すべての量子ビット）。

### 例

以下のコードは、GHZ状態の単一サイト縮退密度行列を取得します。

```jldoctest; setup=:(using Yao)
julia> reg = ghz_state(3)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> density_matrix(reg, (2,)).state
2×2 Matrix{ComplexF64}:
 0.5+0.0im  0.0+0.0im
 0.0-0.0im  0.5+0.0im
```
