```
elsize(tip)
```

Verilen `tip` içinde saklanan [`eltype`](@ref) ardışık elemanları arasındaki bellek adımını bayt cinsinden hesaplar, eğer dizi elemanları yoğun bir şekilde ve uniform bir lineer adımla saklanıyorsa.

# Örnekler

```jldoctest
julia> Base.elsize(rand(Float32, 10))
4
```
