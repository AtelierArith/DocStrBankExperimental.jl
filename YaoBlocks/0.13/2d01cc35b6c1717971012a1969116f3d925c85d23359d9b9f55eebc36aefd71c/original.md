```
EntryTable{IT<:DitStr, ET}
```

A table of ditstring-amplitude, which can be used for e.g. indexing and operator or representing the output of operator indexing.

### Examples

```jldoctest; setup=:(using Yao)
julia> EntryTable([dit"121;3", dit"111;3"], [0.6, 0.8im])
EntryTable{DitStr64{3, 3}, ComplexF64}:
  121 ₍₃₎   0.6 + 0.0im
  111 ₍₃₎   0.0 + 0.8im
```

The following example shows how to create a Hamiltonian and scatter this bit string by this Hamiltonian.

```jldoctest; setup=:(using Yao)
julia> b = kron(X,Z,Y)
nqubits: 3
kron
├─ 1=>X
├─ 2=>Z
└─ 3=>Y

julia> b[:,bit"010"]
EntryTable{DitStr{2, 3, Int64}, ComplexF64}:
  111 ₍₂₎   0.0 - 1.0im

julia> b[:,b[:,bit"010"]]
EntryTable{DitStr{2, 3, Int64}, ComplexF64}:
  010 ₍₂₎   1.0 + 0.0im
```
