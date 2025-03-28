```
LibGit2.FetchOptions
```

Coincide con la estructura [`git_fetch_options`](https://libgit2.org/libgit2/#HEAD/type/git_fetch_options).

Los campos representan:

  * `version`: versión de la estructura en uso, en caso de que esto cambie más adelante. Por ahora, siempre `1`.
  * `callbacks`: callbacks remotos a utilizar durante la obtención.
  * `prune`: si se debe realizar una poda después de la obtención o no. El valor predeterminado es usar la configuración del `GitConfig`.
  * `update_fetchhead`: si se debe actualizar el [`FetchHead`](@ref) después de la obtención. El valor predeterminado es realizar la actualización, que es el comportamiento normal de git.
  * `download_tags`: si se deben descargar las etiquetas presentes en el remoto o no. El valor predeterminado es solicitar las etiquetas para los objetos que se están descargando de todos modos desde el servidor.
  * `proxy_opts`: opciones para conectarse al remoto a través de un proxy. Ver [`ProxyOptions`](@ref). Solo presente en versiones de libgit2 más nuevas o iguales a 0.25.0.
  * `custom_headers`: cualquier encabezado adicional necesario para la obtención. Solo presente en versiones de libgit2 más nuevas o iguales a 0.24.0.
