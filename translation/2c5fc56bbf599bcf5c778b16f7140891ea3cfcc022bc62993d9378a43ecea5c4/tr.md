```
delete!(koleksiyon, anahtar)
```

Verilen anahtar için bir koleksiyondaki eşlemeyi siler, varsa, ve koleksiyonu döner.

# Örnekler

```jldoctest
julia> d = Dict("a"=>1, "b"=>2)
Dict{String, Int64} with 2 entries:
  "b" => 2
  "a" => 1

julia> delete!(d, "b")
Dict{String, Int64} with 1 entry:
  "a" => 1

julia> delete!(d, "b") # d değişmeden kalır
Dict{String, Int64} with 1 entry:
  "a" => 1
```
