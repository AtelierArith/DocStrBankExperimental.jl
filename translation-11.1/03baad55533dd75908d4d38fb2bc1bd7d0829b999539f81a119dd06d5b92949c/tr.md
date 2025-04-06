```
eps(::Type{T}) where T<:AbstractFloat
eps()
```

`T` türünün *makine epsilon* değerini döndürür (`T = Float64` varsayılan olarak). Bu, 1 ile `typeof(one(T))` tarafından temsil edilebilen bir sonraki en büyük değer arasındaki boşluk olarak tanımlanır ve `eps(one(T))` ile eşdeğerdir. (`eps(T)`, `T`'nin *göreceli hata* sınırı olduğundan, [`one`](@ref) gibi "boyutsuz" bir miktardır.)

# Örnekler

```jldoctest
julia> eps()
2.220446049250313e-16

julia> eps(Float32)
1.1920929f-7

julia> 1.0 + eps()
1.0000000000000002

julia> 1.0 + eps()/2
1.0
```
