```
create(
    [ predicate, ] dir, [ tarball ];
    [ skeleton, ] [ portable = false ]
) -> tarball

    predicate :: String --> Bool
    dir       :: AbstractString
    tarball   :: Union{AbstractString, AbstractCmd, IO}
    skeleton  :: Union{AbstractString, AbstractCmd, IO}
    portable  :: Bool
```

Crea un archivo tar ("tarball") del directorio `dir`. El archivo resultante se escribe en la ruta `tarball` o, si no se especifica ninguna ruta, se crea una ruta temporal y se devuelve mediante la llamada a la función. Si `tarball` es un objeto IO, entonces el contenido del tarball se escribe en ese manejador en su lugar (el manejador permanece abierto).

Si se pasa una función `predicate`, se llama a esta en cada ruta del sistema que se encuentra al buscar recursivamente en `dir` y `path` solo se incluye en el tarball si `predicate(path)` es verdadero. Si `predicate(path)` devuelve falso para un directorio, entonces el directorio se excluye por completo: nada bajo ese directorio se incluirá en el archivo.

Si se pasa la palabra clave `skeleton`, entonces el archivo o manejador IO dado se utiliza como un "esqueleto" para generar el tarball. Creas un archivo esqueleto pasando la palabra clave `skeleton` al comando `extract`. Si se llama a `create` con ese archivo esqueleto y los archivos extraídos no han cambiado, se recrea un tarball idéntico. Los argumentos `skeleton` y `predicate` no se pueden usar juntos.

Si la bandera `portable` es verdadera, entonces se verifica la validez de los nombres de ruta en Windows, lo que asegura que no contengan caracteres ilegales o tengan nombres que estén reservados. Consulta https://stackoverflow.com/a/31976060/659248 para más detalles.
