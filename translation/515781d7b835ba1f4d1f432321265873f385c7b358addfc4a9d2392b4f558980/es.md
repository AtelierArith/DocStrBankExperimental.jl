```
get(f::Union{Function, Type}, collection, key)
```

Devuelve el valor almacenado para la clave dada, o si no hay un mapeo para la clave, devuelve `f()`. Usa [`get!`](@ref) para también almacenar el valor predeterminado en el diccionario.

Esto está destinado a ser llamado usando la sintaxis de bloque `do`

```julia
get(dict, key) do
    # valor predeterminado calculado aquí
    time()
end
```
