```
styled(content::AbstractString) -> AnnotatedString
```

Construye una cadena estilizada. Dentro de la cadena, las estructuras `{<specs>:<content>}` aplican el formato a `<content>`, de acuerdo con la lista de especificaciones separadas por comas `<specs>`. Cada especificación puede tomar la forma de un nombre de cara, una especificación de cara en línea, o un par `key=value`. El valor debe estar envuelto por `{...}` si contiene alguno de los caracteres `,=:{}`.

Esta es una equivalente funcional de la macro [`@styled_str`](@ref), solo que sin capacidades de interpolación.
