```
cispi(x)
```

`cis(pi*x)` için daha doğru bir yöntem (özellikle büyük `x` için).

Ayrıca bkz. [`cis`](@ref), [`sincospi`](@ref), [`exp`](@ref), [`angle`](@ref).

# Örnekler

```jldoctest
julia> cispi(10000)
1.0 + 0.0im

julia> cispi(0.25 + 1im)
0.030556854645954562 + 0.03055685464595456im
```

!!! compat "Julia 1.6"
    Bu fonksiyon Julia 1.6 veya daha yenisini gerektirir.

