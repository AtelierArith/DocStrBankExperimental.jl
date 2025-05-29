```
kron(blocks...) -> f(n)
kron(itr) -> f(n)
```

合計のキュービット数を入力として受け取るラムダを返します。

### 例

まだキュービットの数がわからない場合や、ただ怠けているだけの場合でも大丈夫です。

```jldoctest; setup=:(using Yao)
julia> kron(put(1=>X) for _ in 1:2)
(n -> kron(n, ((n  ->  put(n, 1 => X)), (n  ->  put(n, 1 => X)))...))

julia> kron(X for _ in 1:2)
nqubits: 2
kron
├─ 1=>X
└─ 2=>X

julia> kron(1=>X, 3=>Y)
(n -> kron(n, (1 => X, 3 => Y)...))
```
