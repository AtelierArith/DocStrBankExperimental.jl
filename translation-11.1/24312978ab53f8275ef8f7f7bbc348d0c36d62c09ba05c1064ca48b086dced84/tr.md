```
islowercase(c::AbstractChar) -> Bool
```

Bir karakterin küçük harf olup olmadığını test eder (Unicode standardının `Lowercase` türetilmiş özelliğine göre).

Ayrıca [`isuppercase`](@ref) bakınız.

# Örnekler

```jldoctest
julia> islowercase('α')
true

julia> islowercase('Γ')
false

julia> islowercase('❤')
false
```
