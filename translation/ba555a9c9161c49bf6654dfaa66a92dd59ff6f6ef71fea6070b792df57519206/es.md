```
push(repo::GitRepo; kwargs...)
```

Envía actualizaciones a un upstream de `repo`.

Los argumentos de palabra clave son:

  * `remote::AbstractString="origin"`: el nombre del remoto upstream al que enviar.
  * `remoteurl::AbstractString=""`: la URL de `remote`.
  * `refspecs=AbstractString[]`: determina las propiedades del push.
  * `force::Bool=false`: determina si el push será un push forzado, sobrescribiendo la rama remota.
  * `credentials=nothing`: proporciona credenciales y/o configuraciones al autenticar contra un `remote` privado.
  * `callbacks=Callbacks()`: callbacks y cargas útiles proporcionadas por el usuario.

Equivalente a `git push [<remoteurl>|<repo>] [<refspecs>]`.
