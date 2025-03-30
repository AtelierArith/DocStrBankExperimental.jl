```
isabstracttype(T)
```

`T` türünün soyut bir tür olarak ilan edilip edilmediğini belirleyin (yani `abstract type` sözdizimini kullanarak). Bunun `isconcretetype(T)`'nin olumsuzlaması olmadığını unutmayın. Eğer `T` bir tür değilse, `false` döndürün.

# Örnekler

```jldoctest
julia> isabstracttype(AbstractArray)
true

julia> isabstracttype(Vector)
false
```
