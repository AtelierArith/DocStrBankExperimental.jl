```
typemin(T)
```

Verilen (gerçek) sayısal Veri Tipi `T` için temsil edilebilen en düşük değerdir.

Ayrıca bakınız: [`floatmin`](@ref), [`typemax`](@ref), [`eps`](@ref).

# Örnekler

```jldoctest
julia> typemin(Int8)
-128

julia> typemin(UInt32)
0x00000000

julia> typemin(Float16)
-Inf16

julia> typemin(Float32)
-Inf32

julia> nextfloat(-Inf32)  # en küçük sonlu Float32 kayan nokta sayısı
-3.4028235f38
```
