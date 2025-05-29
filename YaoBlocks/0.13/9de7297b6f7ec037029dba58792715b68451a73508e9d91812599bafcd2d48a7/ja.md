```
control(ctrl_locs, target) -> f(n)
```

総アクティブキュービットの数を入力として受け取るラムダを返します。詳細は [`control`](@ref) を参照してください。

### 例

```jldoctest; setup=:(using YaoBlocks)
julia> control((2, 3), 1=>X)
(n -> control(n, (2, 3), 1 => X))

julia> control(2, 1=>X)
(n -> control(n, 2, 1 => X))
```
