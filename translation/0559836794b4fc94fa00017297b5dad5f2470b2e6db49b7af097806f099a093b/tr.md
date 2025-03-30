```
Bidiagonal(dv::V, ev::V, uplo::Symbol) where V <: AbstractVector
```

Verilen diagonal (`dv`) ve off-diagonal (`ev`) vektörlerini kullanarak üst (`uplo=:U`) veya alt (`uplo=:L`) bir bidiagonal matris oluşturur. Sonuç `Bidiagonal` türündedir ve verimli özel lineer çözücüler sağlar, ancak [`convert(Array, _)`](@ref) (veya kısaca `Array(_)`) ile normal bir matrise dönüştürülebilir. `ev`'nin uzunluğu `dv`'nin uzunluğundan bir eksik olmalıdır.

# Örnekler

```jldoctest
julia> dv = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> ev = [7, 8, 9]
3-element Vector{Int64}:
 7
 8
 9

julia> Bu = Bidiagonal(dv, ev, :U) # ev birinci süperdiagonalde
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  7  ⋅  ⋅
 ⋅  2  8  ⋅
 ⋅  ⋅  3  9
 ⋅  ⋅  ⋅  4

julia> Bl = Bidiagonal(dv, ev, :L) # ev birinci altdiagonalde
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅
 7  2  ⋅  ⋅
 ⋅  8  3  ⋅
 ⋅  ⋅  9  4
```
