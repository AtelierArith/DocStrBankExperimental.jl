```
rand_hermitian([T=ComplexF64], N::Int) -> Matrix
```

ランダムなエルミート行列を作成します。

```jldoctest; setup=:(using Yao)
julia> ishermitian(rand_hermitian(2))
true
```
