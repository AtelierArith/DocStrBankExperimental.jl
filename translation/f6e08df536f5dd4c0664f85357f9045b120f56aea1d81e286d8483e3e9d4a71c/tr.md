```
>>>(x, n)
```

Unsigned sağ bit kaydırma operatörü, `x >>> n`. `n >= 0` için, sonuç `x`'in `n` bit sağa kaydırılmasıdır ve `0` ile doldurulur. `n < 0` için, bu `x << -n` ile eşdeğerdir.

[`Unsigned`](@ref) tam sayı türleri için, bu [`>>`](@ref) ile eşdeğerdir. [`Signed`](@ref) tam sayı türleri için, bu `signed(unsigned(x) >> n)` ile eşdeğerdir.

# Örnekler

```jldoctest
julia> Int8(-14) >>> 2
60

julia> bitstring(Int8(-14))
"11110010"

julia> bitstring(Int8(60))
"00111100"
```

[`BigInt`](@ref)ler sonsuz boyutta gibi kabul edilir, bu nedenle doldurmaya gerek yoktur ve bu [`>>`](@ref) ile eşdeğerdir.

Ayrıca bkz. [`>>`](@ref), [`<<`](@ref).
