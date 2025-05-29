```
kron(n, locs_and_blocks::Pair{<:Any, <:AbstractBlock}...) -> KronBlock
```

Returns a `n`-qudit [`KronBlock`](@ref). The inputs contains a list of location-block pairs, where a location can be an integer or a range. It is conceptually a [`chain`](@ref) of [`put`](@ref) block without address conflicts, but it has a richer type information that can be useful for various purposes such as more efficient [`mat`](@ref) function.

Let $I$ be a $2\times 2$ identity matrix, $G$ and $H$ be two $2\times 2$ matrix, the matrix representation of `kron(n, i=>G, j=>H)` (assume $j > i$) is defined as

$$
I^{\otimes n-j} \otimes H \otimes I^{\otimes j-i-1} \otimes G \otimes I^{i-1}
$$

For multiple locations, the expression can be complicated.

### Examples

Use `kron` to construct a `KronBlock`, it will put an `X` gate on the `1`st qubit, and a `Y` gate on the `3`rd qubit.

```jldoctest; setup=:(using Yao)
julia> kron(4, 1=>X, 3=>Y)
nqubits: 4
kron
├─ 1=>X
└─ 3=>Y
```
