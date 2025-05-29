```
kron(blocks::AbstractBlock...)
kron(n, itr)
```

[`KronBlock`](@ref)を返し、総キュービット数は`n`で、`blocks`は量子回路の`n`本のワイヤー上のすべての位置を使用する必要があります。

### 例

小さなブロックを組み合わせて大きなブロックを作成するために、クロネッカー積を使用できます。

```jldoctest; setup=:(using Yao)
julia> kron(X, Y, Z, Z)
nqubits: 4
kron
├─ 1=>X
├─ 2=>Y
├─ 3=>Z
└─ 4=>Z
```
