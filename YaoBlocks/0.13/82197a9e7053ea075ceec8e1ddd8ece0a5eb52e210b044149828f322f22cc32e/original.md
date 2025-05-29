```
chain(blocks...) -> ChainBlock
chain(n) -> ChainBlock
```

Return a [`ChainBlock`](@ref) which chains a list of blocks with the same number of qudits. Let $G_i$ be a sequence of n-qudit blocks, the matrix representation of block `chain(G_1, G_2, ..., G_m)` is

$$
G_m G_{m-1}\ldots G_1
$$

It is almost equivalent to matrix multiplication except the order is reversed. We make its order different from regular matrix multiplication because quantum circuits can be represented more naturally in this form.

### Examples

```jldoctest; setup=:(using Yao)
julia> chain(X, Y, Z)
nqubits: 1
chain
├─ X
├─ Y
└─ Z

julia> chain(2, put(1=>X), put(2=>Y), cnot(2, 1))
nqubits: 2
chain
├─ put on (1)
│  └─ X
├─ put on (2)
│  └─ Y
└─ control(2)
   └─ (1,) X
```
