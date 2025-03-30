```
map!(f, values(dict::AbstractDict))
```

`dict`'i `val`'dan `f(val)`'e dönüştürerek değiştirir. `dict`'in türünün değiştirilemeyeceğini unutmayın: eğer `f(val)` `dict`'in değer türünün bir örneği değilse, mümkünse değer türüne dönüştürülecek ve aksi takdirde bir hata verecektir.

!!! compat "Julia 1.2"
    `map!(f, values(dict::AbstractDict))` Julia 1.2 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> d = Dict(:a => 1, :b => 2)
Dict{Symbol, Int64} with 2 entries:
  :a => 1
  :b => 2

julia> map!(v -> v-1, values(d))
ValueIterator for a Dict{Symbol, Int64} with 2 entries. Values:
  0
  1
```
