```
readeach(io::IO, T)
```

Devuelve un objeto iterable que produce [`read(io, T)`](@ref).

Véase también [`skipchars`](@ref), [`eachline`](@ref), [`readuntil`](@ref).

!!! compat "Julia 1.6"
    `readeach` requiere Julia 1.6 o posterior.


# Ejemplos

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.\n It has many members.\n");

julia> for c in readeach(io, Char)
           c == '\n' && break
           print(c)
       end
JuliaLang is a GitHub organization.
```
