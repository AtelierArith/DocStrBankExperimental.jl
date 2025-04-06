```
valtype(T::Type{<:AbstractArray})
valtype(A::AbstractArray)
```

Bir dizinin değer türünü döndürür. Bu, [`eltype`](@ref) ile aynıdır ve esasen sözlük arayüzü ile uyumluluk için sağlanmıştır.

# Örnekler

```jldoctest
julia> valtype(["one", "two", "three"])
String
```

!!! uyumluluk "Julia 1.2"
    Diziler için bu işlev en az Julia 1.2 gerektirir.

