```
subroutine(n, block, locs)
```

Create a `n`-qudit [`Subroutine`](@ref) block, where the `subblock` is a subprogram of size `m`, and `locs` is a tuple or range of length `m`. It runs a quantum subprogram with smaller size on a subset of locations. While its mathematical definition is the same as the [`put`](@ref) block, while it is more suited for running a larger chunk of circuit.

### Examples

Subroutine is equivalent to [`put`](@ref) a block on given position mathematically, but more efficient and convenient for large blocks.

```jldoctest; setup=:(using Yao)
julia> r = rand_state(3)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> apply!(copy(r), subroutine(X, 1)) ≈ apply!(copy(r), put(1=>X))
true
```

It works for in-contigious locs as well

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
