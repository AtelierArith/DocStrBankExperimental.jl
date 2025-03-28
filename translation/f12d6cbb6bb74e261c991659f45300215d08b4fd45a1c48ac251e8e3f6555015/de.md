```
setindex!(collection, value, key...)
```

Speichert den angegebenen Wert am angegebenen Schlüssel oder Index innerhalb einer Sammlung. Die Syntax `a[i,j,...] = x` wird vom Compiler in `(setindex!(a, x, i, j, ...); x)` umgewandelt.

# Beispiele

```jldoctest
julia> a = Dict("a"=>1)
Dict{String, Int64} mit 1 Eintrag:
  "a" => 1

julia> setindex!(a, 2, "b")
Dict{String, Int64} mit 2 Einträgen:
  "b" => 2
  "a" => 1
```
