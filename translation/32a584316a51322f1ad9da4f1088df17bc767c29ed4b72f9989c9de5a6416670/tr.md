```
get!(koleksiyon, anahtar, varsayılan)
```

Verilen anahtar için saklanan değeri döndür, ya da eğer anahtar için bir eşleme yoksa, `anahtar => varsayılan` sakla ve `varsayılan`ı döndür.

# Örnekler

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> get!(d, "a", 5)
1

julia> get!(d, "d", 4)
4

julia> d
Dict{String, Int64} with 4 entries:
  "c" => 3
  "b" => 2
  "a" => 1
  "d" => 4
```
