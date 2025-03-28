```
extract(
    [ predicate, ] tarball, [ dir ];
    [ skeleton = <none>, ]
    [ copy_symlinks = <auto>, ]
    [ set_permissions = true, ]
) -> dir

    predicate       :: Header --> Bool
    tarball         :: Union{AbstractString, AbstractCmd, IO}
    dir             :: AbstractString
    skeleton        :: Union{AbstractString, AbstractCmd, IO}
    copy_symlinks   :: Bool
    set_permissions :: Bool
```

Extrae un archivo tar ("tarball") ubicado en la ruta `tarball` en el directorio `dir`. Si `tarball` es un objeto IO en lugar de una ruta, entonces el contenido del archivo se leerá desde ese flujo IO. El archivo se extrae en `dir`, que debe ser un directorio vacío existente o una ruta no existente que se puede crear como un nuevo directorio. Si `dir` no se especifica, el archivo se extrae en un directorio temporal que es devuelto por `extract`.

Si se pasa una función `predicate`, se llama a esta en cada objeto `Header` que se encuentra al extraer `tarball` y la entrada solo se extrae si `predicate(hdr)` es verdadero. Esto se puede usar para extraer selectivamente solo partes de un archivo, para omitir entradas que causen que `extract` lance un error, o para registrar lo que se extrae durante el proceso de extracción.

Antes de ser pasado a la función predicate, el objeto `Header` se modifica un poco respecto al encabezado en bruto en el tarball: el campo `path` se normaliza para eliminar entradas `.` y reemplazar múltiples barras consecutivas con una sola barra. Si la entrada tiene tipo `:hardlink`, la ruta del objetivo del enlace se normaliza de la misma manera para que coincida con la ruta de la entrada objetivo; el campo de tamaño se establece en el tamaño de la ruta objetivo (que debe ser un archivo ya visto).

Si se pasa la palabra clave `skeleton`, entonces un "esqueleto" del tarball extraído se escribe en el archivo o manejador IO dado. Este archivo esqueleto se puede usar para recrear un tarball idéntico pasando la palabra clave `skeleton` a la función `create`. Los argumentos `skeleton` y `predicate` no se pueden usar juntos.

Si `copy_symlinks` es `true`, en lugar de extraer enlaces simbólicos como tales, se extraerán como copias de lo que enlazan si son internos al tarball y si es posible hacerlo. Los symlinks no internos, como un enlace a `/etc/passwd`, no se copiarán. Los symlinks que son de alguna manera cíclicos tampoco se copiarán y se omitirán. Por defecto, `extract` detectará si se pueden crear symlinks en `dir` o no y copiará automáticamente los symlinks si no se pueden crear.

Si `set_permissions` es `false`, no se establecen permisos en los archivos extraídos.
