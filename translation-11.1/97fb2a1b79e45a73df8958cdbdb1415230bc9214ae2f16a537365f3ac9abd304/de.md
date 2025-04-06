```
readeach(io::IO, T)
```

Gibt ein iterierbares Objekt zurück, das [`read(io, T)`](@ref) liefert.

Siehe auch [`skipchars`](@ref), [`eachline`](@ref), [`readuntil`](@ref).

!!! compat "Julia 1.6"
    `readeach` erfordert Julia 1.6 oder höher.


# Beispiele

```jldoctest
julia> io = IOBuffer("JuliaLang ist eine GitHub-Organisation.\n Es hat viele Mitglieder.\n");

julia> for c in readeach(io, Char)
           c == '\n' && break
           print(c)
       end
JuliaLang ist eine GitHub-Organisation.
```
