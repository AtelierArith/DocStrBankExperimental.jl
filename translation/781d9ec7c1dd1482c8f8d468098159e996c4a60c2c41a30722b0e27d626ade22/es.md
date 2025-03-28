```
IOBuffer(string::String)
```

Crea un `IOBuffer` de solo lectura sobre los datos subyacentes de la cadena dada.

# Ejemplos

```jldoctest
julia> io = IOBuffer("Haho");

julia> String(take!(io))
"Haho"

julia> String(take!(io))
"Haho"
```
