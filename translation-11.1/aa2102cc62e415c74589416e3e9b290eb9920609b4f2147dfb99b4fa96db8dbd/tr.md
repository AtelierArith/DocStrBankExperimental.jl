```
findlast(pattern::AbstractString, string::AbstractString)
```

`pattern`'ın `string` içindeki son geçişini bulur. [`findprev(pattern, string, lastindex(string))`](@ref) ile eşdeğerdir.

# Örnekler

```jldoctest
julia> findlast("o", "Hello to the world")
15:15

julia> findfirst("Julia", "JuliaLang")
1:5
```
