```
valtype(type)
```

Bir sözlük türünün değer türünü alır. [`eltype`](@ref) ile benzer şekilde davranır.

# Örnekler

```jldoctest
julia> valtype(Dict(Int32(1) => "foo"))
String
```
