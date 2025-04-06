```
copy(A::Transpose)
copy(A::Adjoint)
```

Tembel matris transpozu/adjoint'ını hevesle değerlendirir. Transpozisyonun elemanlara özyinelemeli olarak uygulandığını unutmayın.

Bu işlem, lineer cebir kullanımı için tasarlanmıştır - genel veri manipülasyonu için [`permutedims`](@ref Base.permutedims) bakın, bu özyinelemeli değildir.

# Örnekler

```jldoctest
julia> A = [1 2im; -3im 4]
2×2 Matrix{Complex{Int64}}:
 1+0im  0+2im
 0-3im  4+0im

julia> T = transpose(A)
2×2 transpose(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 1+0im  0-3im
 0+2im  4+0im

julia> copy(T)
2×2 Matrix{Complex{Int64}}:
 1+0im  0-3im
 0+2im  4+0im
```
