```
isdigit(c::AbstractChar) -> Bool
```

Bir karakterin ondalık rakam (0-9) olup olmadığını test eder.

Ayrıca bkz: [`isletter`](@ref).

# Örnekler

```jldoctest
julia> isdigit('❤')
false

julia> isdigit('9')
true

julia> isdigit('α')
false
```
