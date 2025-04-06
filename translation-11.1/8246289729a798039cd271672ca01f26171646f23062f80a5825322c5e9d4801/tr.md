```
inv(x)
```

`x`'in çarpan tersini döndürür, böylece `x*inv(x)` veya `inv(x)*x` [`one(x)`](@ref) (çarpan kimliği) ile yuvarlama hataları göz önüne alındığında eşit olur.

Eğer `x` bir sayı ise, bu esasen `one(x)/x` ile aynıdır, ancak bazı türler için `inv(x)` biraz daha verimli olabilir.

# Örnekler

```jldoctest
julia> inv(2)
0.5

julia> inv(1 + 2im)
0.2 - 0.4im

julia> inv(1 + 2im) * (1 + 2im)
1.0 + 0.0im

julia> inv(2//3)
3//2
```

!!! uyumluluk "Julia 1.2"
    `inv(::Missing)` en az Julia 1.2'yi gerektirir.

