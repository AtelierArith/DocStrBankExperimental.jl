```
cis(A::AbstractMatrix)
```

Kare matris `A` için `exp(im*A)`'nın daha verimli bir yöntemi (özellikle `A` `Hermitian` veya gerçek `Simetrik` ise).

Ayrıca bkz. [`cispi`](@ref), [`sincos`](@ref), [`exp`](@ref).

!!! uyumluluk "Julia 1.7"
    Matrislerle `cis` kullanma desteği Julia 1.7'de eklendi.


# Örnekler

```jldoctest
julia> cis([π 0; 0 π]) ≈ -I
true
```
