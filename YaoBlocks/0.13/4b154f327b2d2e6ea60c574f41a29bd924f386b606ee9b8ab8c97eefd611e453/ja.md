```
swap(n, loc1, loc2)
```

`loc1`と`loc2`をスワップする`n`-キュービット[`Swap`](@ref)ゲートを作成します。

### 例

```jldoctest; setup=:(using Yao)
julia> swap(4, 1, 2)
nqubits: 4
put on (1, 2)
└─ SWAP
```
