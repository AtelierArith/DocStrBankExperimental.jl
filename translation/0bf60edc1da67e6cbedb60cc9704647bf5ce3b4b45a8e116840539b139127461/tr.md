```
signbit(x)
```

`x` değerinin işaretinin negatif olup olmadığını kontrol eder, eğer negatifse `true`, aksi takdirde `false` döner.

Ayrıca bkz. [`sign`](@ref) ve [`copysign`](@ref).

# Örnekler

```jldoctest
julia> signbit(-4)
true

julia> signbit(5)
false

julia> signbit(5.5)
false

julia> signbit(-4.1)
true
```
