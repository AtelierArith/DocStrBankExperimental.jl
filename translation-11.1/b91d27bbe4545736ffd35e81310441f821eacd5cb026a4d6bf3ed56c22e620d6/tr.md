```
first(s::AbstractString, n::Integer)
```

`s`'ninci `n` karakterden oluşan bir dize döndürür.

# Örnekler

```jldoctest
julia> first("∀ϵ≠0: ϵ²>0", 0)
""

julia> first("∀ϵ≠0: ϵ²>0", 1)
"∀"

julia> first("∀ϵ≠0: ϵ²>0", 3)
"∀ϵ≠"
```
