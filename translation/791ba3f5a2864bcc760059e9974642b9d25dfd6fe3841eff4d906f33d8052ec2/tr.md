```
findfirst(pattern::AbstractString, string::AbstractString)
findfirst(pattern::AbstractPattern, string::String)
```

`pattern`'in `string`'deki ilk geçişini bulur. [`findnext(pattern, string, firstindex(s))`](@ref) ile eşdeğerdir.

# Örnekler

```jldoctest
julia> findfirst("z", "Hello to the world") # hiçbir şey döndürmez, ancak REPL'de yazdırılmaz

julia> findfirst("Julia", "JuliaLang")
1:5
```
