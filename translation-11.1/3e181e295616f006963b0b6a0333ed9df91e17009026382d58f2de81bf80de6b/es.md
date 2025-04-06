```
arg_mkdir(f::Function, arg::AbstractString) -> arg
arg_mkdir(f::Function, arg::Nothing) -> mktempdir()
```

La función `arg_mkdir` toma `arg` que debe ser uno de:

  * una ruta a un directorio vacío ya existente,
  * una ruta no existente que puede ser creada como un directorio, o
  * `nothing`, en cuyo caso se crea un directorio temporal.

En todos los casos, se devuelve la ruta al directorio. Si ocurre un error durante `f(arg)`, el directorio se devuelve a su estado original: si ya existía pero estaba vacío, se vaciará; si no existía, se eliminará.
