```
chain(n)
```

空の [`ChainBlock`](@ref) を返し、ブロックのリストのように使用できます。

### 例

```jldoctest; setup=:(using Yao)
julia> chain(2)
nqubits: 2
chain


julia> chain(2; nlevel=3)
nqudits: 2
chain


```
