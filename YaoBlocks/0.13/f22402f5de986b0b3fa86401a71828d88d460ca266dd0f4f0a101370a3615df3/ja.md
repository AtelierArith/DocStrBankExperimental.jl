```
subroutine(n, block, locs)
```

`n`-qudit [`Subroutine`](@ref) ブロックを作成します。ここで、`subblock` はサイズ `m` のサブプログラムであり、`locs` は長さ `m` のタプルまたは範囲です。これは、特定の位置のサブセットで小さいサイズの量子サブプログラムを実行します。その数学的定義は [`put`](@ref) ブロックと同じですが、より大きな回路のチャンクを実行するのに適しています。

### 例

サブルーチンは、与えられた位置での [`put`](@ref) ブロックと数学的に同等ですが、大きなブロックに対してより効率的で便利です。

```jldoctest; setup=:(using Yao)
julia> r = rand_state(3)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> apply!(copy(r), subroutine(X, 1)) ≈ apply!(copy(r), put(1=>X))
true
```

非連続の `locs` に対しても機能します。

```jldoctest; setup=:(using Yao)
julia> r = rand_state(4)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 4/4
    nlevel: 2

julia> cc = subroutine(4, kron(X, Y), (1, 3))
nqubits: 4
Subroutine: (1, 3)
└─ kron
   ├─ 1=>X
   └─ 2=>Y

julia> pp = chain(4, put(1=>X), put(3=>Y))
nqubits: 4
chain
├─ put on (1)
│  └─ X
└─ put on (3)
   └─ Y

julia> apply!(copy(r), cc) ≈ apply!(copy(r), pp)
true
```
