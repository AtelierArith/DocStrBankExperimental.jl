```
cz([n, ]ctrl_locs, location)
```

特別な [`ControlBlock`](@ref)、すなわちアクティブな量子ビットの数 `n` と制御量子ビットの位置 `ctrl_locs`、および `Z` ゲートの `location` を持つ CZ ゲートを返します。詳細は [`cnot`](@ref) を参照してください。

### 例

```jldoctest; setup=:(using Yao)
julia> cz(2, 1, 2)
nqubits: 2
control(1)
└─ (2,) Z
```
