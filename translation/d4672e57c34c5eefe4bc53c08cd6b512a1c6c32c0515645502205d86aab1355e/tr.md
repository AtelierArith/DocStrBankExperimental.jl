```
eigvals!(A; permute::Bool=true, scale::Bool=true, sortby) -> values
```

[`eigvals`](@ref) ile aynı, ancak bir kopya oluşturmak yerine girdi `A`'yı üst üste yazarak yer tasarrufu sağlar. `permute`, `scale` ve `sortby` anahtar kelimeleri [`eigen`](@ref) için olanlarla aynıdır.

!!! not
    Girdi matris `A`, `eigvals!` çağrıldıktan sonra özdeğerlerini içermeyecektir - `A` bir çalışma alanı olarak kullanılır.


# Örnekler

```jldoctest
julia> A = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> eigvals!(A)
2-element Vector{Float64}:
 -0.3722813232690143
  5.372281323269014

julia> A
2×2 Matrix{Float64}:
 -0.372281  -1.0
  0.0        5.37228
```
