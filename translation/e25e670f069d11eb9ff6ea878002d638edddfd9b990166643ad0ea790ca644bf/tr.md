```
isxdigit(c::AbstractChar) -> Bool
```

Bir karakterin geçerli bir onaltılık basamak olup olmadığını test eder. Bunun `0x` ön eki gibi standartta `x`'i içermediğini unutmayın.

# Örnekler

```jldoctest
julia> isxdigit('a')
true

julia> isxdigit('x')
false
```
