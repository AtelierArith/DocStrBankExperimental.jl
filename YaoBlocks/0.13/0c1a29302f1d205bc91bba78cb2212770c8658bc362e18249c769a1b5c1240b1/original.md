```
rand_hermitian([T=ComplexF64], N::Int) -> Matrix
```

Create a random hermitian matrix.

```jldoctest; setup=:(using Yao)
julia> ishermitian(rand_hermitian(2))
true
```
