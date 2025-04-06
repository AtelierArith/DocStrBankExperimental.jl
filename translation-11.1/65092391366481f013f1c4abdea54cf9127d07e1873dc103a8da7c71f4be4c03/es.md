```
Símbolo
```

El tipo de objeto utilizado para representar identificadores en el código julia analizado (ASTs). También se utiliza a menudo como un nombre o etiqueta para identificar una entidad (por ejemplo, como una clave de diccionario). Los `Símbolos` se pueden ingresar utilizando el operador de cita `:`:

```jldoctest
julia> :name
:name

julia> typeof(:name)
Símbolo

julia> x = 42
42

julia> eval(:x)
42
```

Los `Símbolos` también se pueden construir a partir de cadenas u otros valores llamando al constructor `Symbol(x...)`.

Los `Símbolos` son inmutables y su implementación reutiliza el mismo objeto para todos los `Símbolos` con el mismo nombre.

A diferencia de las cadenas, los `Símbolos` son entidades "atómicas" o "escalares" que no admiten iteración sobre caracteres.
