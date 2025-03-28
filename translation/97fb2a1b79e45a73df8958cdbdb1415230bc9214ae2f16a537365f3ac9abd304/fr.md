```
readeach(io::IO, T)
```

Renvoie un objet itérable produisant [`read(io, T)`](@ref).

Voir aussi [`skipchars`](@ref), [`eachline`](@ref), [`readuntil`](@ref).

!!! compat "Julia 1.6"
    `readeach` nécessite Julia 1.6 ou une version ultérieure.


# Exemples

```jldoctest
julia> io = IOBuffer("JuliaLang est une organisation GitHub.\n Elle a de nombreux membres.\n");

julia> for c in readeach(io, Char)
           c == '\n' && break
           print(c)
       end
JuliaLang est une organisation GitHub.
```
