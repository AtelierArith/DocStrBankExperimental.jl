```
typeassert(x, type)
```

`x isa type` değilse bir [`TypeError`](@ref) fırlatır. `x::type` sözdizimi bu fonksiyonu çağırır.

# Örnekler

```jldoctest
julia> typeassert(2.5, Int)
HATA: TypeError: typeassert içinde, beklenen Int64, Float64 türünde bir değer alındı
Stacktrace:
[...]
```
