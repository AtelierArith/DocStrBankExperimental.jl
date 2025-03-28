```
LibGit2.git_url(; kwargs...) -> String
```

Crea una cadena basada en los componentes de la URL proporcionados. Cuando no se proporciona la palabra clave `scheme`, la URL producida utilizará la [sintaxis similar a scp](https://git-scm.com/docs/git-clone#_git_urls_a_id_urls_a) alternativa.

# Palabras clave

  * `scheme::AbstractString=""`: el esquema de la URL que identifica el protocolo a utilizar. Para HTTP usa "http", para SSH usa "ssh", etc. Cuando no se proporciona `scheme`, el formato de salida será "ssh" pero utilizando la sintaxis similar a scp.
  * `username::AbstractString=""`: el nombre de usuario a utilizar en la salida si se proporciona.
  * `password::AbstractString=""`: la contraseña a utilizar en la salida si se proporciona.
  * `host::AbstractString=""`: el nombre del host a utilizar en la salida. Se requiere especificar un nombre de host.
  * `port::Union{AbstractString,Integer}=""`: el número de puerto a utilizar en la salida si se proporciona. No se puede especificar al usar la sintaxis similar a scp.
  * `path::AbstractString=""`: la ruta a utilizar en la salida si se proporciona.

!!! advertencia
    Evita usar contraseñas en URLs. A diferencia de los objetos de credenciales, Julia no puede borrar o destruir de manera segura los datos sensibles después de su uso y la contraseña puede permanecer en la memoria; posiblemente expuesta por una memoria no inicializada.


# Ejemplos

```jldoctest
julia> LibGit2.git_url(username="git", host="github.com", path="JuliaLang/julia.git")
"git@github.com:JuliaLang/julia.git"

julia> LibGit2.git_url(scheme="https", host="github.com", path="/JuliaLang/julia.git")
"https://github.com/JuliaLang/julia.git"

julia> LibGit2.git_url(scheme="ssh", username="git", host="github.com", port=2222, path="JuliaLang/julia.git")
"ssh://git@github.com:2222/JuliaLang/julia.git"
```
