```
tree_hash([ predicate, ] tarball;
          [ algorithm = "git-sha1", ]
          [ skip_empty = false ]) -> hash::String

    predicate  :: Header --> Bool
    tarball    :: Union{AbstractString, AbstractCmd, IO}
    algorithm  :: AbstractString
    skip_empty :: Bool
```

Calcula un valor de hash de árbol para el árbol de archivos que contiene el tarball. Por defecto, esto utiliza el algoritmo de hash de árbol de git con la función de hash segura SHA1 (como las versiones actuales de git). Esto significa que para cualquier tarball cuyo árbol de archivos git pueda representar—es decir, uno que contenga solo archivos, enlaces simbólicos y directorios no vacíos—el valor de hash calculado por esta función será el mismo que el valor de hash que git calcularía para ese árbol de archivos. Ten en cuenta que los tarballs pueden representar árboles de archivos con directorios vacíos, que git no puede almacenar, y esta función puede generar hashes para esos, que, por defecto (ver `skip_empty` a continuación para cómo cambiar este comportamiento), diferirán del hash de un tarball que omite esos directorios vacíos. En resumen, la función de hash coincide con git en todos los árboles que git puede representar, pero extiende (de manera consistente) el dominio de árboles hashables a otros árboles que git no puede representar.

Si se pasa una función `predicate`, se llama a esta en cada objeto `Header` que se encuentra al procesar `tarball` y una entrada solo se hashará si `predicate(hdr)` es verdadero. Esto se puede usar para hashear selectivamente solo partes de un archivo, para omitir entradas que causen que `extract` lance un error, o para registrar lo que se extrae durante el proceso de hashing.

Antes de ser pasada a la función predicate, el objeto `Header` se modifica un poco del encabezado en bruto en el tarball: el campo `path` se normaliza para eliminar entradas `.` y reemplazar múltiples barras diagonales consecutivas con una sola barra diagonal. Si la entrada tiene tipo `:hardlink`, la ruta del objetivo del enlace se normaliza de la misma manera para que coincida con la ruta de la entrada objetivo; el campo de tamaño se establece en el tamaño de la ruta objetivo (que debe ser un archivo ya visto).

Los valores actualmente soportados para `algorithm` son `git-sha1` (el predeterminado) y `git-sha256`, que utiliza el mismo algoritmo básico que `git-sha1` pero reemplaza la función de hash SHA1 con SHA2-256, la función de hash que git comenzará a usar en el futuro (debido a ataques conocidos en SHA1). El soporte para otros algoritmos de hash de árboles de archivos puede ser agregado en el futuro.

La opción `skip_empty` controla si los directorios en el tarball que no contienen recursivamente archivos o enlaces simbólicos se incluyen en el hash o se ignoran. En general, si estás hashando el contenido de un tarball o un árbol de archivos, te importan todos los directorios, no solo los no vacíos, por lo que incluir estos en el hash calculado es el valor predeterminado. Entonces, ¿por qué esta función incluso proporciona la opción de omitir directorios vacíos? Porque git se niega a almacenar directorios vacíos y los ignorará si intentas agregarlos a un repositorio. Así que si calculas un hash de árbol de referencia al agregar archivos a un repositorio git y luego le pides a git el hash de árbol, el valor de hash que obtienes coincidirá con el valor de hash calculado por `tree_hash` con `skip_empty=true`. En otras palabras, esta opción permite que `tree_hash` emule cómo git hasharía un árbol con directorios vacíos. Sin embargo, si estás hashando árboles que pueden contener directorios vacíos (es decir, que no provienen de un repositorio git), se recomienda que los hashes utilizando una herramienta (como esta) que no ignore los directorios vacíos.
