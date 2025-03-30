```
floatmax(T = Float64)
```

`T` türü için temsil edilebilen en büyük sonlu sayıyı döndürür.

Ayrıca bakınız: [`typemax`](@ref), [`floatmin`](@ref), [`eps`](@ref).

# Örnekler

```jldoctest
julia> floatmax(Float16)
Float16(6.55e4)

julia> floatmax(Float32)
3.4028235f38

julia> floatmax()
1.7976931348623157e308

julia> typemax(Float64)
Inf
```
