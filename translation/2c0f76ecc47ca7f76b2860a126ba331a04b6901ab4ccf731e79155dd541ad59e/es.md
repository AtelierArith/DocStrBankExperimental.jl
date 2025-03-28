```
LibGit2.tag_create(repo::GitRepo, tag::AbstractString, commit; kwargs...)
```

Crea una nueva etiqueta git `tag` (por ejemplo, `"v0.5"`) en el repositorio `repo`, en el commit `commit`.

Los argumentos de palabra clave son:

  * `msg::AbstractString=""`: el mensaje para la etiqueta.
  * `force::Bool=false`: si es `true`, las referencias existentes serán sobrescritas.
  * `sig::Signature=Signature(repo)`: la firma del etiquetador.
