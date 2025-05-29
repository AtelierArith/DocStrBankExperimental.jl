```
cnot([n, ]ctrl_locs, location)
```

アクティブな量子ビットの数 `n` と制御量子ビットの位置 `ctrl_locs`、および `X` ゲートの `location` を持つ特別な [`ControlBlock`](@ref)、すなわち CNOT ゲートを返します。

### 例

```jldoctest; setup=:(using YaoBlocks)
julia> cnot(3, (2, 3), 1)
nqubits: 3
control(2, 3)
└─ (1,) X

julia> cnot(2, 1)
(n -> cnot(n, 2, 1))
```
