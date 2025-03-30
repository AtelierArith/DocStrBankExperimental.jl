```
isprint(c::AbstractChar) -> Bool
```

Bir karakterin yazdırılabilir olup olmadığını, boşluklar dahil, ancak kontrol karakterleri hariç test eder.

# Örnekler

```jldoctest
julia> isprint('\x01')
false

julia> isprint('A')
true
```
