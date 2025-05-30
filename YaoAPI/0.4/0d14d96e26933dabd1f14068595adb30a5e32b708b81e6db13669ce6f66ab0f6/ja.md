```
dispatch!(x::AbstractBlock, collection)
```

コレクション内のパラメータをブロックツリー `x` にディスパッチします。

### 引数

  * `x`: パラメータをディスパッチするブロック。
  * `collection`: パラメータのコレクション、例えば数のリスト、`:zero` や `:random` もサポートされており、ここで `:random` は `rand(nparameters(x))` と同等です。

!!! note
    まずコレクション内のパラメータをディスパッチしようとします。


### 例

```jldoctest; setup=:(using Yao)
julia> dispatch!(chain(Rx(0.1), Rz(0.1)), [0.2, 0.3])
nqubits: 1
chain
├─ rot(X, 0.2)
└─ rot(Z, 0.3)

julia> dispatch!(chain(Rx(0.1), Rz(0.2)), :zero)
nqubits: 1
chain
├─ rot(X, 0.0)
└─ rot(Z, 0.0)
```
