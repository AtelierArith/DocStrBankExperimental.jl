```
SymTridiagonal(dv::V, ev::V) where V <: AbstractVector
```

Diyagonal (`dv`) ve ilk alt/üst diyagonal (`ev`) kullanarak simetrik bir tridiagonal matris oluşturur. Sonuç `SymTridiagonal` türündedir ve verimli özel özdeğer çözücüleri sağlar, ancak [`convert(Array, _)`](@ref) (veya kısaca `Array(_)`) ile normal bir matrise dönüştürülebilir.

`SymTridiagonal` blok matrisleri için, `dv` elemanları simetrik hale getirilir. `ev` argümanı üst diyagonal olarak yorumlanır. Alt diyagonal bloklar, karşılık gelen üst diyagonal blokların (materyalize edilmiş) transpozudur.

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

julia> SymTridiagonal(dv, ev)
4×4 SymTridiagonal{Int64, Vector{Int64}}:
 1  7  ⋅  ⋅
 7  2  8  ⋅
 ⋅  8  3  9
 ⋅  ⋅  9  4

julia> A = SymTridiagonal(fill([1 2; 3 4], 3), fill([1 2; 3 4], 2));

julia> A[1,1]
2×2 Symmetric{Int64, Matrix{Int64}}:
 1  2
 2  4

julia> A[1,2]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> A[2,1]
2×2 Matrix{Int64}:
 1  3
 2  4
```
