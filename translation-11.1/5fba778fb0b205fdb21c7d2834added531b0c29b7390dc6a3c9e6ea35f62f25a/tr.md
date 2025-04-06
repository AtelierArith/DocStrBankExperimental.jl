```
Bool <: Integer
```

Boolean türü, `true` ve `false` değerlerini içerir.

`Bool`, bir tür sayı gibidir: `false` sayısal olarak `0`'a, `true` ise sayısal olarak `1`'e eşittir. Dahası, `false`, [`NaN`](@ref) ve [`Inf`](@ref) karşısında çarpan olarak "güçlü sıfır" işlevi görür:

```jldoctest
julia> [true, false] == [1, 0]
true

julia> 42.0 + true
43.0

julia> 0 .* (NaN, Inf, -Inf)
(NaN, NaN, NaN)

julia> false .* (NaN, Inf, -Inf)
(0.0, 0.0, -0.0)
```

[`if`](@ref) ve diğer koşullu ifadeler yalnızca `Bool` kabul eder. Julia'da "doğruluk" değerleri yoktur.

Karşılaştırmalar genellikle `Bool` döner ve yayılmış karşılaştırmalar [`BitArray`](@ref) yerine `Array{Bool}` dönebilir.

```jldoctest
julia> [1 2 3 4 5] .< pi
1×5 BitMatrix:
 1  1  1  0  0

julia> map(>(pi), [1 2 3 4 5])
1×5 Matrix{Bool}:
 0  0  0  1  1
```

Ayrıca [`trues`](@ref), [`falses`](@ref), [`ifelse`](@ref) bakınız.
