```
filter(f, itr::SkipMissing{<:AbstractArray})
```

Verilen `SkipMissing` iteratörü tarafından sarılmış diziye benzer bir vektör döndürür, ancak tüm eksik öğeler ve `f`'nin `false` döndürdüğü öğeler kaldırılır.

!!! compat "Julia 1.2"
    Bu yöntem Julia 1.2 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> x = [1 2; missing 4]
2×2 Matrix{Union{Missing, Int64}}:
 1         2
  missing  4

julia> filter(isodd, skipmissing(x))
1-element Vector{Int64}:
 1
```
