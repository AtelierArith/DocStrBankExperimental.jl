```
isperm(v) -> Bool
```

`v` geçerli bir permütasyon ise `true` döndür.

# Örnekler

```jldoctest
julia> isperm([1; 2])
true

julia> isperm([1; 3])
false
```
