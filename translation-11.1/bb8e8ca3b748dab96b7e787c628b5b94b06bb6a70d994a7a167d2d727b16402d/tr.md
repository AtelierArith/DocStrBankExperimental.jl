```
last(s::AbstractString, n::Integer)
```

`s`'nin son `n` karakterinden oluşan bir dize alır.

# Örnekler

```jldoctest
julia> last("∀ϵ≠0: ϵ²>0", 0)
""

julia> last("∀ϵ≠0: ϵ²>0", 1)
"0"

julia> last("∀ϵ≠0: ϵ²>0", 3)
"²>0"
```
