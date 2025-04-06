```
rmul!(A::AbstractArray, b::Number)
```

Bir diziyi `A` bir skalar `b` ile ölçeklendirir ve `A`'yı yerinde yazar. Skaların soldan çarpılması için [`lmul!`](@ref) kullanın. Ölçekleme işlemi, `A`'nın bir elemanı ile `b` arasındaki çarpma [`*`](@ref) anlamlarını dikkate alır. Özellikle, bu durum `NaN` ve `±Inf` gibi sonlu olmayan sayılarla çarpma işlemlerine de uygulanır.

!!! compat "Julia 1.1"
    Julia 1.1'den önce, `A`'daki `NaN` ve `±Inf` girişleri tutarsız bir şekilde ele alınıyordu.


# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rmul!(A, 2)
2×2 Matrix{Int64}:
 2  4
 6  8

julia> rmul!([NaN], 0.0)
1-element Vector{Float64}:
 NaN
```
