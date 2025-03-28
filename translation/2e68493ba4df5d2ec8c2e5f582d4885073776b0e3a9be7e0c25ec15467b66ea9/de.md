```
getindex(collection, key...)
```

Ruft den Wert(e) ab, die am angegebenen Schlüssel oder Index innerhalb einer Sammlung gespeichert sind. Die Syntax `a[i,j,...]` wird vom Compiler in `getindex(a, i, j, ...)` umgewandelt.

Siehe auch [`get`](@ref), [`keys`](@ref), [`eachindex`](@ref).

# Beispiele

```jldoctest
julia> A = Dict("a" => 1, "b" => 2)
Dict{String, Int64} mit 2 Einträgen:
  "b" => 2
  "a" => 1

julia> getindex(A, "a")
1
```
