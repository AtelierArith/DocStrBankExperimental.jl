```
put(n::Int, locations => subblock) => PutBlock
```

Create a `n`-qudit [`PutBlock`](@ref). The second argument is a pair of locations and subblock, where the locations can be a tuple, an integer or a range and the subblock size should match the length of locations. Let $I$ be a $2\times 2$ identity matrix and $G$ be a $2\times 2$ matrix, the matrix representation of `put(n, i=>G)` is defined as

$$
I^{\otimes n-i} \otimes G \otimes I^{\otimes i-1}
$$

For multiple locations, the expression can be complicated,  which corresponds to the matrix representation of multi-qubit gate applied on `n`-qubit space in quantum computing.

### Examples

```jldoctest; setup=:(using Yao)
julia> put(4, 1=>X)
nqubits: 4
put on (1)
└─ X
```

If you want to put a multi-qubit gate on specific locations, you need to write down all possible locations.

```jldoctest; setup=:(using Yao)
julia> put(4, (1, 3)=>kron(X, Y))
nqubits: 4
put on (1, 3)
└─ kron
   ├─ 1=>X
   └─ 2=>Y
```

The outter locations creates a scope which make it seems to be a contiguous two qubits for the block inside `PutBlock`.

!!! tips
    It is better to use [`subroutine`](@ref) instead of `put` for large blocks, since put will use the matrix of its contents directly instead of making use of what's in it. `put` is more efficient for small blocks.

