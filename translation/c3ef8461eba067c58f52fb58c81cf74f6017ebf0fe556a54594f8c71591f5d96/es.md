```
fetch(repo::GitRepo; kwargs...)
```

Obtiene actualizaciones de un upstream del repositorio `repo`.

Los argumentos de palabra clave son:

  * `remote::AbstractString="origin"`: qué remoto, especificado por nombre, de `repo` se va a obtener. Si está vacío, se utilizará la URL para construir un remoto anónimo.
  * `remoteurl::AbstractString=""`: la URL de `remote`. Si no se especifica, se asumirá en función del nombre dado de `remote`.
  * `refspecs=AbstractString[]`: determina las propiedades de la obtención.
  * `credentials=nothing`: proporciona credenciales y/o configuraciones al autenticar contra un `remote` privado.
  * `callbacks=Callbacks()`: callbacks y cargas útiles proporcionados por el usuario.

Equivalente a `git fetch [<remoteurl>|<repo>] [<refspecs>]`.
