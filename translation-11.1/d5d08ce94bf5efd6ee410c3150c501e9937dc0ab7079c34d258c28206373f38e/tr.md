```
iszero(x)
```

`x == zero(x)` ise `true` döner; eğer `x` bir dizi ise, bu `x`'in tüm elemanlarının sıfır olup olmadığını kontrol eder.

Ayrıca bakınız: [`isone`](@ref), [`isinteger`](@ref), [`isfinite`](@ref), [`isnan`](@ref).

# Örnekler

```jldoctest
julia> iszero(0.0)
true

julia> iszero([1, 9, 0])
false

julia> iszero([false, 0, 0])
true
```
