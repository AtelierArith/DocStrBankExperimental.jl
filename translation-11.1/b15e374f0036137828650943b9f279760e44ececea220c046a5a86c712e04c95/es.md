# Reporting and analyzing crashes (segfaults)

¡Así que lograste romper Julia! ¡Felicidades! Aquí se recopilan algunos procedimientos generales que puedes seguir para los síntomas comunes que se presentan cuando algo sale mal. Incluir la información de estos pasos de depuración puede ayudar enormemente a los mantenedores a rastrear un segfault o a tratar de averiguar por qué tu script se está ejecutando más lento de lo esperado.

Si has sido dirigido a esta página, encuentra el síntoma que mejor coincide con lo que estás experimentando y sigue las instrucciones para generar la información de depuración solicitada. Tabla de síntomas:

  * [Segfaults during bootstrap (`sysimg.jl`)](@ref)
  * [Segfaults when running a script](@ref)
  * [Errors during Julia startup](@ref)
  * [Other generic segfaults or unreachables reached](@ref)

## [Version/Environment info](@id dev-version-info)

No importa el error, siempre necesitaremos saber qué versión de Julia estás ejecutando. Cuando Julia se inicia por primera vez, se imprime un encabezado con un número de versión y una fecha. También incluye la salida de `versioninfo()` (exportado de la [`InteractiveUtils`](@ref InteractiveUtils.versioninfo) biblioteca estándar) en cualquier informe que crees:

```@repl
using InteractiveUtils
versioninfo()
```

## Segfaults during bootstrap (`sysimg.jl`)

Los segfaults hacia el final del proceso de `make` al construir Julia son un síntoma común de que algo está mal mientras Julia está preanalizando el corpus de código en la carpeta `base/`. Muchos factores pueden contribuir a que este proceso muera inesperadamente, sin embargo, a menudo se debe a un error en la parte del código C de Julia, y como tal, generalmente debe ser depurado con una compilación de depuración dentro de `gdb`.  Explícitamente:

Crea una compilación de depuración de Julia:

```
$ cd <julia_root>
$ make debug
```

Tenga en cuenta que este proceso probablemente fallará con el mismo error que una invocación normal de `make`, sin embargo, esto creará un ejecutable de depuración que ofrecerá a `gdb` los símbolos de depuración necesarios para obtener trazas de pila precisas. A continuación, ejecute manualmente el proceso de arranque dentro de `gdb`:

```
$ cd base/
$ gdb -x ../contrib/debug_bootstrap.gdb
```

Esto iniciará `gdb`, intentará ejecutar el proceso de arranque utilizando la versión de depuración de Julia y mostrará un backtrace si (cuando) se produzca un fallo de segmentación. Es posible que necesites presionar `<enter>` varias veces para obtener el backtrace completo. Crea un [gist](https://gist.github.com) con el backtrace, el [version info](@ref dev-version-info), y cualquier otra información pertinente que se te ocurra y abre un nuevo [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen) en Github con un enlace al gist.

## Segfaults when running a script

El procedimiento es muy similar a [Segfaults during bootstrap (`sysimg.jl`)](@ref). Crea una compilación de depuración de Julia y ejecuta tu script dentro de un proceso de Julia depurado:

```
$ cd <julia_root>
$ make debug
$ gdb --args usr/bin/julia-debug <path_to_your_script>
```

Tenga en cuenta que `gdb` estará allí, esperando instrucciones. Escriba `r` para ejecutar el proceso y `bt` para generar un backtrace una vez que falle con un segfault:

```
(gdb) r
Starting program: /home/sabae/src/julia/usr/bin/julia-debug ./test.jl
...
(gdb) bt
```

Crea un [gist](https://gist.github.com) con el backtrace, el [version info](@ref dev-version-info), y cualquier otra información pertinente que puedas pensar y abre un nuevo [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen) en Github con un enlace al gist.

## Errors during Julia startup

Ocasionalmente, ocurren errores durante el proceso de inicio de Julia (especialmente al usar distribuciones binarias, en lugar de compilar desde el código fuente) como el siguiente:

```julia
$ julia
exec: error -5
```

Estos errores típicamente indican que algo no se está cargando correctamente muy al principio de la fase de arranque, y nuestra mejor opción para determinar qué está saliendo mal es utilizar herramientas externas para auditar la actividad del disco del proceso `julia`:

  * En Linux, usa `strace`:

    ```
    $ strace julia
    ```
  * En OSX, usa `dtruss`:

    ```
    $ dtruss -f julia
    ```

Crea un [gist](https://gist.github.com) con la salida de `strace`/ `dtruss`, el [version info](@ref dev-version-info), y cualquier otra información pertinente y abre un nuevo [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen) en Github con un enlace al gist.

## Other generic segfaults or unreachables reached

Como se mencionó en otros lugares, `julia` tiene una buena integración con `rr` para generar trazas; esto incluye, en Linux, la capacidad de ejecutar automáticamente `julia` bajo `rr` y compartir la traza después de un fallo. Esto puede ser inmensamente útil al depurar tales fallos y se recomienda encarecidamente al informar problemas de fallos en el repositorio JuliaLang/julia. Para ejecutar `julia` automáticamente bajo `rr`, haz:

```julia
julia --bug-report=rr
```

Para generar el rastro `rr` localmente, pero no compartirlo, puedes hacer:

```julia
julia --bug-report=rr-local
```

Tenga en cuenta que esto solo funciona en Linux. La publicación del blog en [Time Travelling Bug Reporting](https://julialang.org/blog/2020/05/rr/) tiene muchos más detalles.

## Glossary

Se han utilizado algunos términos como abreviaturas en esta guía:

  * `<julia_root>` se refiere al directorio raíz del árbol de fuentes de Julia; por ejemplo, debería contener carpetas como `base`, `deps`, `src`, `test`, etc.....
