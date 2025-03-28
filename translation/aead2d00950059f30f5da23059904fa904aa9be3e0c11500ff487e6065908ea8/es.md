```
LibGit2.PushOptions
```

Coincide con la estructura [`git_push_options`](https://libgit2.org/libgit2/#HEAD/type/git_push_options).

Los campos representan:

  * `version`: versión de la estructura en uso, en caso de que esto cambie más adelante. Por ahora, siempre `1`.
  * `parallelism`: si se debe crear un archivo de paquete, esta variable establece el número de hilos de trabajo que serán generados por el generador de paquetes. Si es `0`, el generador de paquetes ajustará automáticamente el número de hilos a utilizar. El valor predeterminado es `1`.
  * `callbacks`: los callbacks (por ejemplo, para la autenticación con el remoto) que se utilizarán para el push.
  * `proxy_opts`: solo relevante si la versión de LibGit2 es mayor o igual a `0.25.0`. Establece opciones para usar un proxy para comunicarse con un remoto. Consulte [`ProxyOptions`](@ref) para más información.
  * `custom_headers`: solo relevante si la versión de LibGit2 es mayor o igual a `0.24.0`. Encabezados adicionales necesarios para la operación de push.
