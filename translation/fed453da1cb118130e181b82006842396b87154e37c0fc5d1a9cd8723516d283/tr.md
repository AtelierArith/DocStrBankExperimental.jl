```
isspace(c::AbstractChar) -> Bool
```

Bir karakterin herhangi bir boşluk karakteri olup olmadığını test eder. ASCII karakterleri '\t', '\n', '\v', '\f', '\r' ve ' ', Latin-1 karakteri U+0085 ve Unicode kategorisi Zs'deki karakterleri içerir.

# Örnekler

```jldoctest
julia> isspace('\n')
true

julia> isspace('\r')
true

julia> isspace(' ')
true

julia> isspace('\x20')
true
```
