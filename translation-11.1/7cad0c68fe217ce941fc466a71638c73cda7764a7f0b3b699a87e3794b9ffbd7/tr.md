```
keytype(type)
```

Bir sözlük türünün anahtar türünü alır. [`eltype`](@ref) ile benzer şekilde davranır.

# Örnekler

```jldoctest
julia> keytype(Dict(Int32(1) => "foo"))
Int32
```
