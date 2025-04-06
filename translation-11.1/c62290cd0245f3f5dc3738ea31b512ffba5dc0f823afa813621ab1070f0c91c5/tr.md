```
supertypleri(T::Type)
```

`T` ve tüm süper tiplerinin bir demetini `(T, ..., Any)` olarak döndürür; bu, [`supertype`](@ref) fonksiyonuna ardışık çağrılarla belirlenir, `<:` sırasına göre listelenir ve `Any` ile sonlandırılır.

Ayrıca bkz. [`subtypes`](@ref).

# Örnekler

```jldoctest
julia> supertypes(Int)
(Int64, Signed, Integer, Real, Number, Any)
```
