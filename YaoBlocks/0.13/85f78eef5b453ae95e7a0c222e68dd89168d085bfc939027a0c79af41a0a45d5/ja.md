```
repeat(n, subblock::AbstractBlock[, locs]) -> RepeatedBlock{n}
```

`n`-qudit [`RepeatedBlock`](@ref) ブロックを作成します。これは概念的にはすべてのゲートが同じである [`kron`] ブロックです。`locs` が提供されている場合は `locs` で繰り返し、そうでない場合はすべての位置で繰り返します。$G$ を $2\times 2$ 行列とすると、`repeat(n, X)` の行列表現は

$$
X^{\otimes n}
$$

`RepeatedBlock` は、特定のゲートタイプ `X`、`Y`、`Z`、`S`、`T`、`Sdag`、および `Tdag` を繰り返し適用するのを加速するために使用できます。

### 例

これは、各位置に4つのXゲートを配置する繰り返しブロックを作成します。

```jldoctest; setup=:(using Yao)
julia> repeat(4, X)
nqubits: 4
repeat on (1, 2, 3, 4)
└─ X
```

位置を指定することもできます。

```jldoctest; setup=:(using Yao)
julia> repeat(4, X, (1, 2))
nqubits: 4
repeat on (1, 2)
└─ X
```

ただし、繰り返しはゲートをコピーしないため、パラメータを持つゲート（例：`phase(0.1)`）の場合、パラメータは同時に変更されます。

```jldoctest; setup=:(using Yao)
julia> g = repeat(4, phase(0.1))
nqubits: 4
repeat on (1, 2, 3, 4)
└─ phase(0.1)

julia> g.content
phase(0.1)

julia> g.content.theta = 0.2
0.2

julia> g
nqubits: 4
repeat on (1, 2, 3, 4)
└─ phase(0.2)
```

特定のゲートに対して繰り返すことで、速度が向上します。

```julia
julia> reg = rand_state(20);

julia> @time apply!(reg, repeat(20, X));
  0.002252 seconds (5 allocations: 656 bytes)

julia> @time apply!(reg, chain([put(20, i=>X) for i=1:20]));
  0.049362 seconds (82.48 k allocations: 4.694 MiB, 47.11% compilation time)
```
