```
chsubblocks(composite_block, itr)
```

与えられたイテレータ `itr` で [`CompositeBlock`](@ref) のサブブロックを変更します。

### 例

```jldoctest; setup=:(using Yao)
julia> chsubblocks(chain(X, Y, Z), [Z, Z])
nqubits: 1
chain
├─ Z
└─ Z
```
