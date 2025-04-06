```
exp(A::AbstractMatrix)
```

`A` matrisinin üstelini hesaplayın, tanımıyla

$$
e^A = \sum_{n=0}^{\infty} \frac{A^n}{n!}.
$$

Simetrik veya Hermit `A` için, bir özdeğişim ([`eigen`](@ref)) kullanılır, aksi takdirde ölçekleme ve kareleme algoritması seçilir (bkz. [^H05]).

[^H05]: Nicholas J. Higham, "The squaring and scaling method for the matrix exponential revisited", SIAM Journal on Matrix Analysis and Applications, 26(4), 2005, 1179-1193. [doi:10.1137/090768539](https://doi.org/10.1137/090768539)

# Örnekler

```jldoctest
julia> A = Matrix(1.0I, 2, 2)
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0

julia> exp(A)
2×2 Matrix{Float64}:
 2.71828  0.0
 0.0      2.71828
```
