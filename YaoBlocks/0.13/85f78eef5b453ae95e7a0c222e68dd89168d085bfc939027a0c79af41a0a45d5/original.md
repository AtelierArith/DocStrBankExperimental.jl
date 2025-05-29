```
repeat(n, subblock::AbstractBlock[, locs]) -> RepeatedBlock{n}
```

Create a `n`-qudit [`RepeatedBlock`](@ref) block, which is conceptually a [`kron`] block with all gates being the same. If `locs` is provided, repeat on `locs`, otherwise repeat on all locations. Let $G$ be a $2\times 2$ matrix, the matrix representation of `repeat(n, X)` is

$$
X^{\otimes n}
$$

The `RepeatedBlock` can be used to accelerate repeated applying certain gate types: `X`, `Y`, `Z`, `S`, `T`, `Sdag`, and `Tdag`.

### Examples

This will create a repeat block which puts 4 X gates on each location.

```jldoctest; setup=:(using Yao)
julia> repeat(4, X)
nqubits: 4
repeat on (1, 2, 3, 4)
└─ X
```

You can also specify the location

```jldoctest; setup=:(using Yao)
julia> repeat(4, X, (1, 2))
nqubits: 4
repeat on (1, 2)
└─ X
```

But repeat won't copy the gate, thus, if it is a gate with parameter, e.g a `phase(0.1)`, the parameter will change simultaneously.

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

Repeat over certain gates will provide speed up.

```julia
julia> reg = rand_state(20);

julia> @time apply!(reg, repeat(20, X));
  0.002252 seconds (5 allocations: 656 bytes)

julia> @time apply!(reg, chain([put(20, i=>X) for i=1:20]));
  0.049362 seconds (82.48 k allocations: 4.694 MiB, 47.11% compilation time)
```
