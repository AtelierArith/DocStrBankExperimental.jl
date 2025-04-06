```
isuppercase(c::AbstractChar) -> Bool
```

Bir karakterin büyük harf olup olmadığını test eder (Unicode standardının `Uppercase` türetilmiş özelliğine göre).

Ayrıca [`islowercase`](@ref) bakınız.

# Örnekler

```jldoctest
julia> isuppercase('γ')
false

julia> isuppercase('Γ')
true

julia> isuppercase('❤')
false
```
