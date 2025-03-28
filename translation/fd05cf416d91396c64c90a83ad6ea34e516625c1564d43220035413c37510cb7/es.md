```
list(tarball; [ strict = true ]) -> Vector{Header}
list(callback, tarball; [ strict = true ])

    callback  :: Header, [ <data> ] --> Any
    tarball   :: Union{AbstractString, AbstractCmd, IO}
    strict    :: Bool
```

Lista el contenido de un archivo tar ("tarball") ubicado en la ruta `tarball`. Si `tarball` es un manejador de IO, lee el contenido del tar desde ese flujo. Devuelve un vector de estructuras `Header`. Consulta [`Header`](@ref) para más detalles.

Si se proporciona un `callback`, en lugar de devolver un vector de encabezados, se llama al callback en cada `Header`. Esto puede ser útil si el número de elementos en el tarball es grande o si deseas examinar elementos antes de un error en el tarball. Si la función `callback` puede aceptar un segundo argumento de tipo `Vector{UInt8}` o `Vector{Pair{Symbol, String}}`, entonces se llamará con una representación de los datos del encabezado en bruto, ya sea como un único vector de bytes o como un vector de pares que mapean nombres de campo a los datos en bruto para ese campo (si estos campos están concatenados, el resultado es los datos en bruto del encabezado).

Por defecto, `list` generará un error si encuentra algún contenido del tarball que la función `extract` se negaría a extraer. Con `strict=false`, omitirá estas verificaciones y listará todo el contenido del archivo tar, ya sea que `extract` los extraiga o no. Ten cuidado, ya que los tarballs maliciosos pueden hacer todo tipo de cosas astutas e inesperadas para intentar engañarte y hacer algo malo.

Si el argumento `tarball` es un archivo esqueleto (consulta `extract` y `create`), entonces `list` detectará eso a partir del encabezado del archivo y listará o iterará apropiadamente los encabezados del archivo esqueleto.
