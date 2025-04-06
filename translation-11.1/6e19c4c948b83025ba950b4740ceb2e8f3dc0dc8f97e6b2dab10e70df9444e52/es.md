```
LibGit2.CloneOptions
```

Coincide con la estructura [`git_clone_options`](https://libgit2.org/libgit2/#HEAD/type/git_clone_options).

Los campos representan:

  * `version`: versión de la estructura en uso, en caso de que esto cambie más adelante. Por ahora, siempre `1`.
  * `checkout_opts`: Las opciones para realizar el checkout del remoto como parte de la clonación.
  * `fetch_opts`: Las opciones para realizar la obtención previa al checkout del remoto como parte de la clonación.
  * `bare`: Si `0`, clona el repositorio remoto completo. Si es diferente de cero, realiza una clonación bare, en la que no hay una copia local de los archivos fuente en el repositorio y el [`gitdir`](@ref) y [`workdir`](@ref) son los mismos.
  * `localclone`: Indicador de si clonar una base de datos de objetos local o hacer una obtención. El valor predeterminado es dejar que git decida. No utilizará el transporte consciente de git para una clonación local, pero lo usará para URLs que comienzan con `file://`.
  * `checkout_branch`: El nombre de la rama a la que hacer checkout. Si es una cadena vacía, se hará checkout de la rama predeterminada del remoto.
  * `repository_cb`: Un callback opcional que se utilizará para crear el *nuevo* repositorio en el que se realiza la clonación.
  * `repository_cb_payload`: La carga útil para el callback del repositorio.
  * `remote_cb`: Un callback opcional utilizado para crear el [`GitRemote`](@ref) antes de hacer la clonación desde él.
  * `remote_cb_payload`: La carga útil para el callback remoto.
