```
UniformScaling{T<:Number}
```

Bir skalar ile kimlik operatörünün çarpımı olarak tanımlanan genel boyutlu uniform ölçekleme operatörü, `λ*I`. Açık bir `boyut` olmadan, birçok durumda bir matris gibi davranır ve bazı dizinlemeleri destekler. Ayrıca [`I`](@ref) için de bakınız.

!!! compat "Julia 1.6"
    Aralıklar kullanarak dizinleme, Julia 1.6 itibarıyla mevcuttur.


# Örnekler

```jldoctest
julia> J = UniformScaling(2.)
UniformScaling{Float64}
2.0*I

julia> A = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> J*A
2×2 Matrix{Float64}:
 2.0  4.0
 6.0  8.0

julia> J[1:2, 1:2]
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  2.0
```
