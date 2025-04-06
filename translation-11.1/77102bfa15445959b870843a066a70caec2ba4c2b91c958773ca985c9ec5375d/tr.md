```
lmul!(a::Number, B::AbstractArray)
```

Bir diziyi `B` bir skalar `a` ile ölçeklendirir ve `B`'yi yerinde günceller. Skaların sağdan çarpılması için [`rmul!`](@ref) kullanın. Ölçeklendirme işlemi, `a` ile `B`'nin bir elemanı arasındaki çarpmanın [`*`](@ref) anlamlarını dikkate alır. Özellikle, bu durum `NaN` ve `±Inf` gibi sonlu olmayan sayılarla çarpma işlemlerine de uygulanır.

!!! compat "Julia 1.1"
    Julia 1.1'den önce, `B`'deki `NaN` ve `±Inf` girişleri tutarsız bir şekilde ele alınıyordu.


# Örnekler

```jldoctest
julia> B = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> lmul!(2, B)
2×2 Matrix{Int64}:
 2  4
 6  8

julia> lmul!(0.0, [Inf])
1-element Vector{Float64}:
 NaN
```
