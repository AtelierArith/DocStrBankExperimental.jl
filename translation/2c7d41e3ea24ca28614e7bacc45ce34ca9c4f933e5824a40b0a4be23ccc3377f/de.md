```
position(en)
```

Holen Sie sich die aktuelle Position eines Streams.

# Beispiele

```jldoctest
julia> io = IOBuffer("JuliaLang ist eine GitHub-Organisation.");

julia> seek(io, 5);

julia> position(io)
5

julia> skip(io, 10);

julia> position(io)
15

julia> seekend(io);

julia> position(io)
35
```
