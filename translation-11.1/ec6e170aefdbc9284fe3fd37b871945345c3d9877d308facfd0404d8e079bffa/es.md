```
LibGit2.ProxyOptions
```

Opciones para conectarse a través de un proxy.

Coincide con la estructura [`git_proxy_options`](https://libgit2.org/libgit2/#HEAD/type/git_proxy_options).

Los campos representan:

  * `version`: versión de la estructura en uso, en caso de que esto cambie más adelante. Por ahora, siempre `1`.
  * `proxytype`: un `enum` para el tipo de proxy a utilizar. Definido en [`git_proxy_t`](https://libgit2.org/libgit2/#HEAD/type/git_proxy_t). El enum correspondiente en Julia es `GIT_PROXY` y tiene los valores:

      * `PROXY_NONE`: no intentar la conexión a través de un proxy.
      * `PROXY_AUTO`: intentar averiguar la configuración del proxy a partir de la configuración de git.
      * `PROXY_SPECIFIED`: conectarse utilizando la URL dada en el campo `url` de esta estructura.

    El valor predeterminado es detectar automáticamente el tipo de proxy.
  * `url`: la URL del proxy.
  * `credential_cb`: un puntero a una función de callback que se llamará si el remoto requiere autenticación para conectarse.
  * `certificate_cb`: un puntero a una función de callback que se llamará si la verificación del certificado falla. Esto permite al usuario decidir si continuar o no con la conexión. Si la función devuelve `1`, se permitirá la conexión. Si devuelve `0`, no se permitirá la conexión. Se puede usar un valor negativo para devolver errores.
  * `payload`: la carga útil que se proporcionará a las dos funciones de callback.

# Ejemplos

```julia-repl
julia> fo = LibGit2.FetchOptions(
           proxy_opts = LibGit2.ProxyOptions(url = Cstring("https://my_proxy_url.com")))

julia> fetch(remote, "master", options=fo)
```
