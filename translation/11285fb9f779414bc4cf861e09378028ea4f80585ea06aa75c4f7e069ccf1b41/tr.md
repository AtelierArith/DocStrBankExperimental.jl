```
isone(x)
```

`x == one(x)` ise `true` döner; eğer `x` bir dizi ise, bu `x`'in bir kimlik matris olup olmadığını kontrol eder.

# Örnekler

```jldoctest
julia> isone(1.0)
true

julia> isone([1 0; 0 2])
false

julia> isone([1 0; 0 true])
true
```
