```
BigInt(x)
```

Arbitrary hassasiyetli bir tam sayı oluşturur. `x`, bir `Int` (veya bir `Int`'e dönüştürülebilen herhangi bir şey) olabilir. Bu tür için olağan matematiksel operatörler tanımlıdır ve sonuçlar [`BigInt`](@ref) olarak yükseltilir.

Örnekler, [`parse`](@ref) aracılığıyla dizelerden veya `big` dize literalini kullanarak oluşturulabilir.

# Örnekler

```jldoctest
julia> parse(BigInt, "42")
42

julia> big"313"
313

julia> BigInt(10)^19
10000000000000000000
```
