```
string(n::Integer; base::Integer = 10, pad::Integer = 1)
```

Bir tam sayıyı `n` verilen `base`'de bir dizeye dönüştürür, isteğe bağlı olarak doldurulacak basamak sayısını belirtir.

Ayrıca bkz. [`digits`](@ref), [`bitstring`](@ref), [`count_zeros`](@ref).

# Örnekler

```jldoctest
julia> string(5, base = 13, pad = 4)
"0005"

julia> string(-13, base = 5, pad = 4)
"-0023"
```
