```
filter(f, itr::SkipMissing{<:AbstractArray})
```

Gibt einen Vektor zurück, der dem Array ähnelt, das vom gegebenen `SkipMissing`-Iterator umschlossen ist, jedoch mit allen fehlenden Elementen und denen, für die `f` `false` zurückgibt, entfernt.

!!! compat "Julia 1.2"
    Diese Methode erfordert Julia 1.2 oder höher.


# Beispiele

```jldoctest
julia> x = [1 2; missing 4]
2×2 Matrix{Union{Missing, Int64}}:
 1         2
  missing  4

julia> filter(isodd, skipmissing(x))
1-element Vector{Int64}:
 1
```
