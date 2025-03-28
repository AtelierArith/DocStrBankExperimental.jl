```
take!(b::IOBuffer)
```

Erhalten Sie den Inhalt eines `IOBuffer` als Array. Danach wird der `IOBuffer` auf seinen ursprünglichen Zustand zurückgesetzt.

# Beispiele

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang ist eine GitHub-Organisation.", " Es hat viele Mitglieder.")
56

julia> String(take!(io))
"JuliaLang ist eine GitHub-Organisation. Es hat viele Mitglieder."
```
