```
first(coll)
```

Bir yineleyici koleksiyonun ilk öğesini alır. Boş olsa bile bir [`AbstractRange`](@ref) başlangıç noktasını döndürür.

Ayrıca bakınız: [`only`](@ref), [`firstindex`](@ref), [`last`](@ref).

# Örnekler

```jldoctest
julia> first(2:2:10)
2

julia> first([1; 2; 3; 4])
1
```
