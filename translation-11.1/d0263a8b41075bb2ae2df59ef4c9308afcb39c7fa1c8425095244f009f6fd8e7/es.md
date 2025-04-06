# printf() and stdio in the Julia runtime

## [Libuv wrappers for stdio](@id Libuv-wrappers-for-stdio)

`julia.h` define [libuv](https://docs.libuv.org) envolturas para los flujos de `stdio.h`:

```c
uv_stream_t *JL_STDIN;
uv_stream_t *JL_STDOUT;
uv_stream_t *JL_STDERR;
```

... y funciones de salida correspondientes:

```c
int jl_printf(uv_stream_t *s, const char *format, ...);
int jl_vprintf(uv_stream_t *s, const char *format, va_list args);
```

Estas funciones `printf` son utilizadas por los archivos `.c` en los directorios `src/` y `cli/` donde se necesita stdio para asegurar que el almacenamiento en búfer de salida se maneje de manera unificada.

In special cases, like signal handlers, where the full libuv infrastructure is too heavy, `jl_safe_printf()` can be used to [`write(2)`](@ref) directly to `STDERR_FILENO`:

```c
void jl_safe_printf(const char *str, ...);
```

## Interface between JL_STD* and Julia code

[`Base.stdin`](@ref), [`Base.stdout`](@ref) y [`Base.stderr`](@ref) están vinculados a los flujos libuv `JL_STD*` definidos en el tiempo de ejecución.

La función `__init__()` de Julia (en `base/sysimg.jl`) llama a `reinit_stdio()` (en `base/stream.jl`) para crear objetos de Julia para [`Base.stdin`](@ref), [`Base.stdout`](@ref) y [`Base.stderr`](@ref).

`reinit_stdio()` utiliza [`ccall`](@ref) para recuperar punteros a `JL_STD*` y llama a `jl_uv_handle_type()` para inspeccionar el tipo de cada flujo. Luego crea un objeto `Base.IOStream`, `Base.TTY` o `Base.PipeEndpoint` de Julia para representar cada flujo, por ejemplo:

```
$ julia -e 'println(typeof((stdin, stdout, stderr)))'
Tuple{Base.TTY,Base.TTY,Base.TTY}

$ julia -e 'println(typeof((stdin, stdout, stderr)))' < /dev/null 2>/dev/null
Tuple{IOStream,Base.TTY,IOStream}

$ echo hello | julia -e 'println(typeof((stdin, stdout, stderr)))' | cat
Tuple{Base.PipeEndpoint,Base.PipeEndpoint,Base.TTY}
```

El [`Base.read`](@ref) y [`Base.write`](@ref) métodos para estos flujos utilizan [`ccall`](@ref) para llamar a los envoltorios de libuv en `src/jl_uv.c`, p. ej.:

```
stream.jl: function write(s::IO, p::Ptr, nb::Integer)
               -> ccall(:jl_uv_write, ...)
  jl_uv.c:          -> int jl_uv_write(uv_stream_t *stream, ...)
                        -> uv_write(uvw, stream, buf, ...)
```

## printf() during initialization

Los flujos de libuv de los que depende `jl_printf()` etc., no están disponibles hasta la mitad de la inicialización del tiempo de ejecución (ver `init.c`, `init_stdio()`). Los mensajes de error o advertencias que necesitan ser impresos antes de esto se envían a la función `fwrite()` de la biblioteca estándar de C mediante el siguiente mecanismo:

En `sys.c`, los punteros de flujo `JL_STD*` están inicializados estáticamente a constantes enteras: `STD*_FILENO (0, 1 y 2)`. En `jl_uv.c`, la función `jl_uv_puts()` verifica su argumento `uv_stream_t* stream` y llama a `fwrite()` si el flujo está configurado en `STDOUT_FILENO` o `STDERR_FILENO`.

Esto permite un uso uniforme de `jl_printf()` a lo largo del tiempo de ejecución, independientemente de si alguna parte particular del código es accesible antes de que se complete la inicialización.

## [Legacy `ios.c` library](@id Legacy-ios.c-library)

La biblioteca `src/support/ios.c` se hereda de [femtolisp](https://github.com/JeffBezanson/femtolisp). Proporciona entrada/salida de archivos con búferes multiplataforma y búferes temporales en memoria.

`ios.c` todavía se utiliza en:

  * `src/flisp/*.c`
  * `src/dump.c` – para la entrada/salida de archivos de serialización y para los búferes de memoria.
  * `src/staticdata.c` – para la entrada/salida de archivos de serialización y para los búferes de memoria.
  * `base/iostream.jl` – para IO de archivos (ver `base/fs.jl` para el equivalente de libuv).

El uso de `ios.c` en estos módulos es mayormente autónomo y está separado del sistema de E/S de libuv. Sin embargo, hay [one place](https://github.com/JuliaLang/julia/blob/master/src/flisp/print.c#L654) donde femtolisp llama a `jl_printf()` a través de un flujo `ios_t` heredado.

Hay un hack en `ios.h` que hace que el campo `ios_t.bm` se alinee con el `uv_stream_t.type` y asegura que los valores utilizados para `ios_t.bm` no se superpongan con los valores válidos de `UV_HANDLE_TYPE`. Esto permite que los punteros `uv_stream_t` apunten a flujos `ios_t`.

Esto es necesario porque el llamador de `jl_printf()`, `jl_static_show()`, recibe un flujo `ios_t` a través de la función `fl_print()` de femtolisp. La función `jl_uv_puts()` de Julia tiene un manejo especial para esto:

```c
if (stream->type > UV_HANDLE_TYPE_MAX) {
    return ios_write((ios_t*)stream, str, n);
}
```
