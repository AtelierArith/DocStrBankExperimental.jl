```
rand_unitary([T=ComplexF64], N::Int) -> Matrix
```

Create a random unitary matrix.

### Examples

```jldoctest; setup=:(using Yao)
julia> isunitary(rand_unitary(2))
true

julia> eltype(rand_unitary(ComplexF32, 2))
ComplexF32 (alias for Complex{Float32})
```
