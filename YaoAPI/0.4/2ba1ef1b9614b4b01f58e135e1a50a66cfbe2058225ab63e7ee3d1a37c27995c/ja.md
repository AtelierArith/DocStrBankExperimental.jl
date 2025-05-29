```
subblocks(x)
```

合成ブロックのサブブロックのイテレータを返します。デフォルトは空です。

### 例

```jldoctest; setup=:(using Yao)
julia> subblocks(chain(X, Y, Z))
3-element Vector{AbstractBlock{2}}:
 X
 Y
 Z
```
