```
fetch(c::Channel)
```

Wartet auf und gibt (ohne zu entfernen) das erste verfügbare Element aus dem `Channel` zurück. Hinweis: `fetch` wird bei einem unbuffered (0-Größe) `Channel` nicht unterstützt.

# Beispiele

Pufferkanal:

```jldoctest
julia> c = Channel(3) do ch
           foreach(i -> put!(ch, i), 1:3)
       end;

julia> fetch(c)
1

julia> collect(c)  # Element wird nicht entfernt
3-element Vector{Any}:
 1
 2
 3
```
