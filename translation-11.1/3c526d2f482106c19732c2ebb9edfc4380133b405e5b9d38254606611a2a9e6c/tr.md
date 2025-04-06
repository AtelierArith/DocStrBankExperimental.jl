```
get(collection, key, default)
```

Verilen anahtar için saklanan değeri döndürür veya anahtar için bir eşleme yoksa verilen varsayılan değeri döndürür.

!!! compat "Julia 1.7"
    Tuple'lar ve sayılar için, bu fonksiyon en az Julia 1.7 gerektirir.


# Örnekler

```jldoctest
julia> d = Dict("a"=>1, "b"=>2);

julia> get(d, "a", 3)
1

julia> get(d, "c", 3)
3
```
