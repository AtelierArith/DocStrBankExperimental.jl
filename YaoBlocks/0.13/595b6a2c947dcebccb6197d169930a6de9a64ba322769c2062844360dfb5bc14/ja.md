```
Scale{S <: Union{Number, Val}, D, BT <: AbstractBlock{D}} <: TagBlock{BT, D}
Scale(factor, block)
```

スカラー因子でブロックを乗算します。因子は数値または `Val` であることができます。因子が数値の場合、それは動的に変更可能なパラメータと見なされます。因子が `Val` の場合、それは定数と見なされます。

### 例

```jldoctest; setup=:(using YaoBlocks)
julia> 2 * X
[scale: 2] X

julia> im * Z
[+im] Z

julia> -im * Z
[-im] Z

julia> -Z
[-] Z
```
