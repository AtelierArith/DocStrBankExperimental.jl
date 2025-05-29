```
basis(register) -> UnitRange
```

Returns an `UnitRange` of the all the bits in the Hilbert space of given register.

```jldoctest; setup=:(using Yao)
julia> collect(basis(rand_state(3)))
8-element Vector{DitStr{2, 3, Int64}}:
 000 ₍₂₎
 001 ₍₂₎
 010 ₍₂₎
 011 ₍₂₎
 100 ₍₂₎
 101 ₍₂₎
 110 ₍₂₎
 111 ₍₂₎
```
