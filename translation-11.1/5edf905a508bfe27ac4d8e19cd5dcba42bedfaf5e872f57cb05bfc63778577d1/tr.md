```
ispow2(n::Number) -> Bool
```

`n`'nin bir tam sayı iki kuvveti olup olmadığını test eder.

Ayrıca bkz. [`count_ones`](@ref), [`prevpow`](@ref), [`nextpow`](@ref).

# Örnekler

```jldoctest
julia> ispow2(4)
true

julia> ispow2(5)
false

julia> ispow2(4.5)
false

julia> ispow2(0.25)
true

julia> ispow2(1//8)
true
```

!!! compat "Julia 1.6"
    Julia 1.6'da `Integer` olmayan argümanlar için destek eklendi.

