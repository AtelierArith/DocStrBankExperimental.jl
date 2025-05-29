```
swap(loc1, loc2) -> f(n)
```

アクティブな量子ビットの総数を入力として受け取るラムダを作成します。`swap(n, loc1, loc2)`の遅延カリー版です。詳細は[`Swap`](@ref)を参照してください。

### 例

```jldoctest; setup=:(using Yao)
julia> swap(1, 2)
(n -> swap(n, 1, 2))
```
