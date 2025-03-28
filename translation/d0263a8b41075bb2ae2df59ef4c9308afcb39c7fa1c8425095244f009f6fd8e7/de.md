# printf() and stdio in the Julia runtime

## [Libuv wrappers for stdio](@id Libuv-wrappers-for-stdio)

`julia.h` definiert [libuv](https://docs.libuv.org) Wrapper für die `stdio.h` Streams:

```c
uv_stream_t *JL_STDIN;
uv_stream_t *JL_STDOUT;
uv_stream_t *JL_STDERR;
```

... und entsprechende Ausgabefunktionen:

```c
int jl_printf(uv_stream_t *s, const char *format, ...);
int jl_vprintf(uv_stream_t *s, const char *format, va_list args);
```

Diese `printf`-Funktionen werden von den `.c`-Dateien in den `src/`- und `cli/`-Verzeichnissen verwendet, wo immer stdio benötigt wird, um sicherzustellen, dass die Ausgabepufferung einheitlich behandelt wird.

In special cases, like signal handlers, where the full libuv infrastructure is too heavy, `jl_safe_printf()` can be used to [`write(2)`](@ref) directly to `STDERR_FILENO`:

```c
void jl_safe_printf(const char *str, ...);
```

## Interface between JL_STD* and Julia code

[`Base.stdin`](@ref), [`Base.stdout`](@ref) und [`Base.stderr`](@ref) sind an die `JL_STD*` libuv-Streams gebunden, die zur Laufzeit definiert sind.

Julias `__init__()`-Funktion (in `base/sysimg.jl`) ruft `reinit_stdio()` (in `base/stream.jl`) auf, um Julia-Objekte für [`Base.stdin`](@ref), [`Base.stdout`](@ref) und [`Base.stderr`](@ref) zu erstellen.

`reinit_stdio()` verwendet [`ccall`](@ref), um Zeiger auf `JL_STD*` abzurufen, und ruft `jl_uv_handle_type()` auf, um den Typ jedes Streams zu überprüfen. Anschließend erstellt es ein Julia `Base.IOStream`, `Base.TTY` oder `Base.PipeEndpoint` Objekt, um jeden Stream darzustellen, z. B.:

```
$ julia -e 'println(typeof((stdin, stdout, stderr)))'
Tuple{Base.TTY,Base.TTY,Base.TTY}

$ julia -e 'println(typeof((stdin, stdout, stderr)))' < /dev/null 2>/dev/null
Tuple{IOStream,Base.TTY,IOStream}

$ echo hello | julia -e 'println(typeof((stdin, stdout, stderr)))' | cat
Tuple{Base.PipeEndpoint,Base.PipeEndpoint,Base.TTY}
```

Die [`Base.read`](@ref) und [`Base.write`](@ref) Methoden für diese Streams verwenden [`ccall`](@ref), um libuv-Wrapper in `src/jl_uv.c` aufzurufen, z.B.:

```
stream.jl: function write(s::IO, p::Ptr, nb::Integer)
               -> ccall(:jl_uv_write, ...)
  jl_uv.c:          -> int jl_uv_write(uv_stream_t *stream, ...)
                        -> uv_write(uvw, stream, buf, ...)
```

## printf() during initialization

Die von `jl_printf()` usw. abhängigen libuv-Streams sind erst zur Mitte der Initialisierung der Laufzeit verfügbar (siehe `init.c`, `init_stdio()`). Fehlermeldungen oder Warnungen, die vorher ausgegeben werden müssen, werden durch den folgenden Mechanismus an die Standard-C-Bibliotheksfunktion `fwrite()` weitergeleitet:

In `sys.c` sind die `JL_STD*` Stream-Pointer statisch auf Ganzzahlkonstanten initialisiert: `STD*_FILENO (0, 1 und 2)`. In `jl_uv.c` überprüft die Funktion `jl_uv_puts()` ihr Argument `uv_stream_t* stream` und ruft `fwrite()` auf, wenn der Stream auf `STDOUT_FILENO` oder `STDERR_FILENO` gesetzt ist.

Dies ermöglicht eine einheitliche Verwendung von `jl_printf()` während der Laufzeit, unabhängig davon, ob ein bestimmter Codeabschnitt vor Abschluss der Initialisierung erreichbar ist oder nicht.

## [Legacy `ios.c` library](@id Legacy-ios.c-library)

Die `src/support/ios.c` Bibliothek wird von [femtolisp](https://github.com/JeffBezanson/femtolisp) abgeleitet. Sie bietet plattformübergreifende gepufferte Datei-I/O und temporäre Puffer im Arbeitsspeicher.

`ios.c` wird immer noch verwendet von:

  * `src/flisp/*.c`
  * `src/dump.c` – für die Serialisierung von Datei-I/O und für Speicherpuffer.
  * `src/staticdata.c` – für die Serialisierungsdatei IO und für Speicherpuffer.
  * `base/iostream.jl` – für Datei-I/O (siehe `base/fs.jl` für das libuv-Äquivalent).

Die Verwendung von `ios.c` in diesen Modulen ist größtenteils eigenständig und vom libuv I/O-System getrennt. Es gibt jedoch [one place](https://github.com/JuliaLang/julia/blob/master/src/flisp/print.c#L654), wo femtolisp über einen Legacy `ios_t`-Stream auf `jl_printf()` zugreift.

Es gibt einen Hack in `ios.h`, der das Feld `ios_t.bm` mit dem `uv_stream_t.type` ausrichtet und sicherstellt, dass die Werte, die für `ios_t.bm` verwendet werden, sich nicht mit gültigen `UV_HANDLE_TYPE`-Werten überschneiden. Dies ermöglicht es `uv_stream_t`-Zeigern, auf `ios_t`-Streams zu zeigen.

Dies ist erforderlich, da der Aufrufer von `jl_printf()`, `jl_static_show()`, einen `ios_t`-Stream von femtolisp's `fl_print()`-Funktion übergeben bekommt. Julias Funktion `jl_uv_puts()` hat dafür eine spezielle Behandlung:

```c
if (stream->type > UV_HANDLE_TYPE_MAX) {
    return ios_write((ios_t*)stream, str, n);
}
```
