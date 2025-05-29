```
cache(x[, level=1; recursive=false])
```

与えられたブロック `x` で [`CachedBlock`](@ref) を作成します。これは、最初に [`mat`](@ref) を呼び出すときに `x` の行列をキャッシュし、その後の計算でキャッシュされた行列を使用します。

### 例

```jldoctest; setup=:(using YaoBlocks)
julia> cache(control(3, 1, 2=>X))
nqubits: 3
[cached] control(1)
   └─ (2,) X


julia> chain(cache(control(3, 1, 2=>X)), repeat(H))
nqubits: 3
chain
└─ [cached] control(1)
      └─ (2,) X

```
