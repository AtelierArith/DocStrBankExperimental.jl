```
Tridiagonal(dl::V, d::V, du::V) where V <: AbstractVector
```

İlk alt diyagonal, diyagonal ve ilk üst diyagonal kullanılarak bir üçlü matris oluşturur. Sonuç `Tridiagonal` türündedir ve verimli özel lineer çözücüler sağlar, ancak [`convert(Array, _)`](@ref) (veya kısaca `Array(_)`) ile normal bir matrise dönüştürülebilir. `dl` ve `du`'nun uzunlukları, `d`'nin uzunluğundan bir eksik olmalıdır.

!!! not
    Alt diyagonal `dl` ve üst diyagonal `du` birbirine referans vermemelidir. Eğer referans verme tespit edilirse, yapıcı `du`'nun bir kopyasını argüman olarak kullanacaktır.


# Örnekler

```jldoctest
julia> dl = [1, 2, 3];

julia> du = [4, 5, 6];

julia> d = [7, 8, 9, 0];

julia> Tridiagonal(dl, d, du)
4×4 Tridiagonal{Int64, Vector{Int64}}:
 7  4  ⋅  ⋅
 1  8  5  ⋅
 ⋅  2  9  6
 ⋅  ⋅  3  0
```
