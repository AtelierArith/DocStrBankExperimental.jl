```
keytype(T::Type{<:AbstractArray})
keytype(A::AbstractArray)
```

Bir dizinin anahtar türünü döndürür. Bu, `keys(...)` sonucunun [`eltype`](@ref) ile eşdeğerdir ve esasen sözlük arayüzü ile uyumluluk için sağlanmıştır.

# Örnekler

```jldoctest
julia> keytype([1, 2, 3]) == Int
true

julia> keytype([1 2; 3 4])
CartesianIndex{2}
```

!!! compat "Julia 1.2"
    Diziler için bu işlev en az Julia 1.2'yi gerektirir.

