```
rewrite(
    [ predicate, ] old_tarball, [ new_tarball ];
    [ portable = false, ]
) -> new_tarball

    predicate   :: Header --> Bool
    old_tarball :: Union{AbstractString, AbstractCmd, IO}
    new_tarball :: Union{AbstractString, AbstractCmd, IO}
    portable    :: Bool
```

Reescribe `old_tarball` al formato estándar que genera `create`, mientras también verifica que no contenga nada que cause que `extract` genere un error. Esto es funcionalmente equivalente a hacer

```
Tar.create(Tar.extract(predicate, old_tarball), new_tarball)
```

Sin embargo, nunca extrae nada en el disco y en su lugar utiliza la función `seek` para navegar por los datos del antiguo tarball. Si no se pasa un argumento `new_tarball`, el nuevo tarball se escribe en un archivo temporal cuyo camino se devuelve.

Si se pasa una función `predicate`, se llama a esta en cada objeto `Header` que se encuentra al extraer `old_tarball` y la entrada se omite a menos que `predicate(hdr)` sea verdadero. Esto se puede usar para reescribir selectivamente solo partes de un archivo, para omitir entradas que causarían que `extract` lanzara un error, o para registrar qué contenido se encuentra durante el proceso de reescritura.

Antes de ser pasado a la función predicate, el objeto `Header` se modifica un poco del encabezado en bruto en el tarball: el campo `path` se normaliza para eliminar entradas `.` y reemplazar múltiples barras consecutivas con una sola barra. Si la entrada tiene tipo `:hardlink`, la ruta del objetivo del enlace se normaliza de la misma manera para que coincida con la ruta de la entrada objetivo; el campo de tamaño se establece en el tamaño de la ruta objetivo (que debe ser un archivo ya visto).

Si la bandera `portable` es verdadera, entonces los nombres de las rutas se verifican para su validez en Windows, lo que asegura que no contengan caracteres ilegales o tengan nombres que estén reservados. Consulta https://stackoverflow.com/a/31976060/659248 para más detalles.
