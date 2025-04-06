```
fetch(c::Channel)
```

Espera y devuelve (sin eliminar) el primer elemento disponible del `Channel`. Nota: `fetch` no es compatible con un `Channel` sin búfer (tamaño 0).

# Ejemplos

Canal con búfer:

```jldoctest
julia> c = Channel(3) do ch
           foreach(i -> put!(ch, i), 1:3)
       end;

julia> fetch(c)
1

julia> collect(c)  # el elemento no se elimina
3-element Vector{Any}:
 1
 2
 3
```
