```
promote(xs...)
```

Tüm argümanları ortak bir türe dönüştürün ve hepsini (bir demet olarak) geri döndürün. Hiçbir argüman dönüştürülemezse, bir hata oluşur.

Ayrıca bakınız: [`promote_type`](@ref), [`promote_rule`](@ref).

# Örnekler

```jldoctest
julia> promote(Int8(1), Float16(4.5), Float32(4.1))
(1.0f0, 4.5f0, 4.1f0)

julia> promote_type(Int8, Float16, Float32)
Float32

julia> reduce(Base.promote_typejoin, (Int8, Float16, Float32))
Real

julia> promote(1, "x")
HATA: Int64 ve String türlerinin tanıtımı herhangi bir argümanı değiştirmeyi başaramadı
[...]

julia> promote_type(Int, String)
Any
```
