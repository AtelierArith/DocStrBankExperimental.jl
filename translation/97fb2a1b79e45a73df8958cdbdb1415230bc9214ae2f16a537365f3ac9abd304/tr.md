```
readeach(io::IO, T)
```

Bir [`read(io, T)`](@ref) döndüren bir iterable nesne sağlar.

Ayrıca [`skipchars`](@ref), [`eachline`](@ref), [`readuntil`](@ref) ile de bakabilirsiniz.

!!! compat "Julia 1.6"
    `readeach`, Julia 1.6 veya daha yeni bir sürüm gerektirir.


# Örnekler

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.\n It has many members.\n");

julia> for c in readeach(io, Char)
           c == '\n' && break
           print(c)
       end
JuliaLang is a GitHub organization.
```
