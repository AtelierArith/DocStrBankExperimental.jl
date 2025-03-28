# printf() and stdio in the Julia runtime

## [Libuv wrappers for stdio](@id Libuv-wrappers-for-stdio)

`julia.h` définit [libuv](https://docs.libuv.org) des wrappers pour les flux `stdio.h` :

```c
uv_stream_t *JL_STDIN;
uv_stream_t *JL_STDOUT;
uv_stream_t *JL_STDERR;
```

... et les fonctions de sortie correspondantes :

```c
int jl_printf(uv_stream_t *s, const char *format, ...);
int jl_vprintf(uv_stream_t *s, const char *format, va_list args);
```

Ces fonctions `printf` sont utilisées par les fichiers `.c` dans les répertoires `src/` et `cli/` chaque fois que stdio est nécessaire pour garantir que la mise en mémoire tampon de la sortie est gérée de manière unifiée.

In special cases, like signal handlers, where the full libuv infrastructure is too heavy, `jl_safe_printf()` can be used to [`write(2)`](@ref) directly to `STDERR_FILENO`:

```c
void jl_safe_printf(const char *str, ...);
```

## Interface between JL_STD* and Julia code

[`Base.stdin`](@ref), [`Base.stdout`](@ref) et [`Base.stderr`](@ref) sont liés aux flux libuv `JL_STD*` définis dans le runtime.

La fonction `__init__()` de Julia (dans `base/sysimg.jl`) appelle `reinit_stdio()` (dans `base/stream.jl`) pour créer des objets Julia pour [`Base.stdin`](@ref), [`Base.stdout`](@ref) et [`Base.stderr`](@ref).

`reinit_stdio()` utilise [`ccall`](@ref) pour récupérer des pointeurs vers `JL_STD*` et appelle `jl_uv_handle_type()` pour inspecter le type de chaque flux. Il crée ensuite un objet `Base.IOStream`, `Base.TTY` ou `Base.PipeEndpoint` de Julia pour représenter chaque flux, par exemple :

```
$ julia -e 'println(typeof((stdin, stdout, stderr)))'
Tuple{Base.TTY,Base.TTY,Base.TTY}

$ julia -e 'println(typeof((stdin, stdout, stderr)))' < /dev/null 2>/dev/null
Tuple{IOStream,Base.TTY,IOStream}

$ echo hello | julia -e 'println(typeof((stdin, stdout, stderr)))' | cat
Tuple{Base.PipeEndpoint,Base.PipeEndpoint,Base.TTY}
```

Les méthodes [`Base.read`](@ref) et [`Base.write`](@ref) pour ces flux utilisent [`ccall`](@ref) pour appeler les wrappers libuv dans `src/jl_uv.c`, par exemple :

```
stream.jl: function write(s::IO, p::Ptr, nb::Integer)
               -> ccall(:jl_uv_write, ...)
  jl_uv.c:          -> int jl_uv_write(uv_stream_t *stream, ...)
                        -> uv_write(uvw, stream, buf, ...)
```

## printf() during initialization

Les flux libuv sur lesquels s'appuient `jl_printf()` etc., ne sont pas disponibles avant le milieu de l'initialisation du runtime (voir `init.c`, `init_stdio()`). Les messages d'erreur ou les avertissements qui doivent être imprimés avant cela sont dirigés vers la fonction `fwrite()` de la bibliothèque standard C par le mécanisme suivant :

Dans `sys.c`, les pointeurs de flux `JL_STD*` sont initialisés statiquement avec des constantes entières : `STD*_FILENO (0, 1 et 2)`. Dans `jl_uv.c`, la fonction `jl_uv_puts()` vérifie son argument `uv_stream_t* stream` et appelle `fwrite()` si le flux est défini sur `STDOUT_FILENO` ou `STDERR_FILENO`.

Cela permet une utilisation uniforme de `jl_printf()` tout au long de l'exécution, que ce soit ou non qu'un morceau de code particulier soit accessible avant que l'initialisation ne soit terminée.

## [Legacy `ios.c` library](@id Legacy-ios.c-library)

La bibliothèque `src/support/ios.c` est héritée de [femtolisp](https://github.com/JeffBezanson/femtolisp). Elle fournit des entrées/sorties de fichiers tamponnées multiplateformes et des tampons temporaires en mémoire.

`ios.c` est toujours utilisé par :

  * `src/flisp/*.c`
  * `src/dump.c` – pour l'IO de fichiers de sérialisation et pour les tampons mémoire.
  * `src/staticdata.c` – pour l'entrée/sortie de fichiers de sérialisation et pour les tampons mémoire.
  * `base/iostream.jl` – pour l'IO de fichiers (voir `base/fs.jl` pour l'équivalent libuv).

L'utilisation de `ios.c` dans ces modules est principalement autonome et séparée du système d'E/S de libuv. Cependant, il y a [one place](https://github.com/JuliaLang/julia/blob/master/src/flisp/print.c#L654) où femtolisp appelle `jl_printf()` avec un flux `ios_t` hérité.

Il y a un hack dans `ios.h` qui aligne le champ `ios_t.bm` avec le `uv_stream_t.type` et garantit que les valeurs utilisées pour `ios_t.bm` ne se chevauchent pas avec les valeurs `UV_HANDLE_TYPE` valides. Cela permet aux pointeurs `uv_stream_t` de pointer vers des flux `ios_t`.

Ceci est nécessaire car l'appelant de `jl_printf()` `jl_static_show()` reçoit un flux `ios_t` par la fonction `fl_print()` de femtolisp. La fonction `jl_uv_puts()` de Julia a un traitement spécial pour cela :

```c
if (stream->type > UV_HANDLE_TYPE_MAX) {
    return ios_write((ios_t*)stream, str, n);
}
```
