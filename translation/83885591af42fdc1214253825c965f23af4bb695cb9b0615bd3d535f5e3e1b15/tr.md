```
issubnormal(f) -> Bool
```

Bir kayan nokta sayısının altnormal olup olmadığını test eder.

Bir IEEE kayan nokta sayısı, üstel bitleri sıfır ve anlam değeri sıfır değilse [altnormal](https://en.wikipedia.org/wiki/Subnormal_number) olarak kabul edilir.

# Örnekler

```jldoctest
julia> floatmin(Float32)
1.1754944f-38

julia> issubnormal(1.0f-37)
false

julia> issubnormal(1.0f-38)
true
```
