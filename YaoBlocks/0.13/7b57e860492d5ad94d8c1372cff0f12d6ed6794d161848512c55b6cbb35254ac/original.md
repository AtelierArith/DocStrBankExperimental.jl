```
map_address(block::AbstractBlock, info::AddressInfo) -> AbstractBlock
```

map the locations in `block` to target locations.

# Example

`map_address` can be used to embed a sub-circuit to a larger one.

```jldoctest; setup=:(using YaoBlocks)
julia> c = chain(5, repeat(H, 1:5), put(2=>X), kron(1=>X, 3=>Y))
nqubits: 5
chain
├─ repeat on (1, 2, 3, 4, 5)
│  └─ H
├─ put on (2)
│  └─ X
└─ kron
   ├─ 1=>X
   └─ 3=>Y


julia> map_address(c, AddressInfo(10, [6,7,8,9,10]))
nqubits: 10
chain
├─ repeat on (6, 7, 8, 9, 10)
│  └─ H
├─ put on (7)
│  └─ X
└─ kron
   ├─ 6=>X
   └─ 8=>Y
```
