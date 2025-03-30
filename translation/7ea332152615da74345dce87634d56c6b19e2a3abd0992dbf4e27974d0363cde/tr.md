```
eigvals!(A, B; sortby) -> values
```

[`eigvals`](@ref) ile aynı, ancak kopyalar oluşturmak yerine giriş `A` (ve `B`) üzerine yazarak alan tasarrufu sağlar.

!!! not
    Giriş matrisleri `A` ve `B`, `eigvals!` çağrıldıktan sonra özdeğerlerini içermeyecektir. Çalışma alanı olarak kullanılırlar.


# Örnekler

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> eigvals!(A, B)
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> A
2×2 Matrix{Float64}:
 -0.0  -1.0
  1.0  -0.0

julia> B
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
