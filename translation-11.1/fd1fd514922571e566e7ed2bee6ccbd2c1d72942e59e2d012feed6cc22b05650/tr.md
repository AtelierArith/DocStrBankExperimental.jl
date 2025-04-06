```
typemax(T)
```

Verilen (gerçek) sayısal `DataType` için temsil edilebilen en yüksek değeri döndürür.

Ayrıca bakınız: [`floatmax`](@ref), [`typemin`](@ref), [`eps`](@ref).

# Örnekler

```jldoctest
julia> typemax(Int8)
127

julia> typemax(UInt32)
0xffffffff

julia> typemax(Float64)
Inf

julia> typemax(Float32)
Inf32

julia> floatmax(Float32)  # en büyük sonlu Float32 kayan nokta sayısı
3.4028235f38
```
