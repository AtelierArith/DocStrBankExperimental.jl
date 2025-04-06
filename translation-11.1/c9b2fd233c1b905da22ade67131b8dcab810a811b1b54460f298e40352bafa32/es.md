```
instances(T::Type)
```

Devuelve una colección de todas las instancias del tipo dado, si es aplicable. Principalmente utilizado para tipos enumerados (ver `@enum`).

# Ejemplos

```jldoctest
julia> @enum Color red blue green

julia> instances(Color)
(red, blue, green)
```
