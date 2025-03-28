```
addface!(name::Symbol => default::Face)
```

Crea una nueva cara con el nombre `name`. Siempre que no exista ya una cara con este nombre, `default` se añade tanto a `FACES``.default` como (una copia de) a `FACES`.`current`, con el valor actual devuelto.

Si la cara `name` ya existe, se devuelve `nothing`.

# Ejemplos

```jldoctest; setup = :(import StyledStrings: Face, addface!)
julia> addface!(:mypkg_myface => Face(slant=:italic, underline=true))
Face (muestra)
         slant: italic
     underline: true
```
