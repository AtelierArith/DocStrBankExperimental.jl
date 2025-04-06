```
SubString(s::AbstractString, i::Integer, j::Integer=lastindex(s))
SubString(s::AbstractString, r::UnitRange{<:Integer})
```

[`getindex`](@ref) gibi, ancak bir kopya yapmak yerine `s` ana dizesi içindeki `i:j` veya `r` aralığında bir görünüm döndürür.

[`@views`](@ref) makrosu, bir kod bloğundaki herhangi bir dize dilimini `s[i:j]` alt dizelerine `SubString(s, i, j)` dönüştürür.

# Örnekler

```jldoctest
julia> SubString("abc", 1, 2)
"ab"

julia> SubString("abc", 1:2)
"ab"

julia> SubString("abc", 2)
"bc"
```
