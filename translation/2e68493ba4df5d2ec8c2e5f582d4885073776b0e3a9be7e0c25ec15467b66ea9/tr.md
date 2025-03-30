```
getindex(koleksiyon, anahtar...)
```

Verilen anahtar veya indeks içindeki koleksiyonda saklanan değer(ler)i alır. `a[i,j,...]` sözdizimi derleyici tarafından `getindex(a, i, j, ...)` olarak dönüştürülür.

Ayrıca bkz. [`get`](@ref), [`keys`](@ref), [`eachindex`](@ref).

# Örnekler

```jldoctest
julia> A = Dict("a" => 1, "b" => 2)
Dict{String, Int64} with 2 entries:
  "b" => 2
  "a" => 1

julia> getindex(A, "a")
1
```
