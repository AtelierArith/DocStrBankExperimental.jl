# Initialization of the Julia runtime

Wie führt die Julia-Laufzeit `julia -e 'println("Hello World!")'` aus?

## `main()`

Die Ausführung beginnt bei [`main()` in `cli/loader_exe.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_exe.c), das `jl_load_repl()` in [`cli/loader_lib.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_lib.c) aufruft, das einige Bibliotheken lädt und schließlich [`jl_repl_entrypoint()` in `src/jlapi.c`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c) aufruft.

`jl_repl_entrypoint()` ruft [`libsupport_init()`](https://github.com/JuliaLang/julia/blob/master/src/support/libsupportinit.c) auf, um die C-Bibliothekslokalisierung festzulegen und die "ios"-Bibliothek zu initialisieren (siehe [`ios_init_stdstreams()`](https://github.com/JuliaLang/julia/blob/master/src/support/ios.c) und [Legacy `ios.c` library](@ref Legacy-ios.c-library)).

Nächster [`jl_parse_opts()`](https://github.com/JuliaLang/julia/blob/master/src/jloptions.c) wird aufgerufen, um Befehlszeilenoptionen zu verarbeiten. Beachten Sie, dass `jl_parse_opts()` nur mit Optionen umgeht, die die Codegenerierung oder die frühe Initialisierung betreffen. Andere Optionen werden später von [`exec_options()` in `base/client.jl`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) behandelt.

`jl_parse_opts()` speichert Befehlszeilenoptionen in der [global `jl_options` struct](https://github.com/JuliaLang/julia/blob/master/src/julia.h).

## `julia_init()`

[`julia_init()` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c) wird von `main()` aufgerufen und ruft [`_julia_init()` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c) auf.

`_julia_init()` beginnt damit, `libsupport_init()` erneut aufzurufen (es tut beim zweiten Mal nichts).

[`restore_signals()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) wird aufgerufen, um die Signalhandler-Maske auf Null zu setzen.

[`jl_resolve_sysimg_location()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) durchsucht konfigurierte Pfade nach dem Basis-System-Image. Siehe [Building the Julia system image](@ref Building-the-Julia-system-image).

[`jl_gc_init()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) richtet Zuteilungspools und Listen für schwache Referenzen, erhaltene Werte und Finalisierung ein.

[`jl_init_frontend()`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) lädt und initialisiert ein vorcompiliertes Femtolisp-Image, das den Scanner/Parser enthält.

[`jl_init_types()`](https://github.com/JuliaLang/julia/blob/master/src/jltypes.c) erstellt `jl_datatype_t` Typbeschreibungsobjekte für die [built-in types defined in `julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h). z.B.

```c
jl_any_type = jl_new_abstracttype(jl_symbol("Any"), core, NULL, jl_emptysvec);
jl_any_type->super = jl_any_type;

jl_type_type = jl_new_abstracttype(jl_symbol("Type"), core, jl_any_type, jl_emptysvec);

jl_int32_type = jl_new_primitivetype(jl_symbol("Int32"), core,
                                     jl_any_type, jl_emptysvec, 32);
```

[`jl_init_tasks()`](https://github.com/JuliaLang/julia/blob/master/src/task.c) erstellt das `jl_datatype_t* jl_task_type` Objekt; initialisiert die globale `jl_root_task` Struktur; und setzt `jl_current_task` auf die Root-Aufgabe.

[`jl_init_codegen()`](https://github.com/JuliaLang/julia/blob/master/src/codegen.cpp) initialisiert die [LLVM library](https://llvm.org).

[`jl_init_serializer()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) initialisiert 8-Bit-Serialisierungstags für eingebaute `jl_value_t`-Werte.

Wenn keine sysimg-Datei (`!jl_options.image_file`) vorhanden ist, werden die Module `Core` und `Main` erstellt und `boot.jl` wird ausgewertet:

`jl_core_module = jl_new_module(jl_symbol("Core"))` erstellt das Julia `Core`-Modul.

[`jl_init_intrinsic_functions()`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp) erstellt ein neues Julia-Modul `Intrinsics`, das die Konstanten `jl_intrinsic_type`-Symbole enthält. Diese definieren einen ganzzahligen Code für jede [intrinsic function](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp). [`emit_intrinsic()`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp) übersetzt diese Symbole in LLVM-Anweisungen während der Codegenerierung.

[`jl_init_primitives()`](https://github.com/JuliaLang/julia/blob/master/src/builtins.c) verbindet C-Funktionen mit Julia-Funktionssymbolen. z.B. ist das Symbol `Core.:(===)()` an den C-Funktionszeiger `jl_f_is()` gebunden, indem `add_builtin_func("===", jl_f_is)` aufgerufen wird.

[`jl_new_main_module()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) erstellt das globale "Main"-Modul und setzt `jl_current_task->current_module = jl_main_module`.

Hinweis: `_julia_init()` [then sets](https://github.com/JuliaLang/julia/blob/master/src/init.c) `jl_root_task->current_module = jl_core_module`. `jl_root_task` ist zu diesem Zeitpunkt ein Alias von `jl_current_task`, sodass das von `jl_new_main_module()` oben gesetzte `current_module` überschrieben wird.

[`jl_load("boot.jl", sizeof("boot.jl"))`](https://github.com/JuliaLang/julia/blob/master/src/init.c) ruft [`jl_parse_eval_all`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) auf, das wiederholt [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) aufruft, um [`boot.jl`](https://github.com/JuliaLang/julia/blob/master/base/boot.jl) auszuführen. <!– TODO – in eval vertiefen? –>

[`jl_get_builtin_hooks()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) initialisiert globale C-Zeiger auf Julia-Globals, die in `boot.jl` definiert sind.

[`jl_init_box_caches()`](https://github.com/JuliaLang/julia/blob/master/src/datatype.c) reserviert globale verpackte Ganzzahlwertobjekte für Werte bis zu 1024. Dies beschleunigt die Zuweisung von verpackten Ganzzahlen später. z.B.:

```c
jl_value_t *jl_box_uint8(uint32_t x)
{
    return boxed_uint8_cache[(uint8_t)x];
}
```

[`_julia_init()` iterates](https://github.com/JuliaLang/julia/blob/master/src/init.c) über das `jl_core_module->bindings.table`, um nach `jl_datatype_t` Werten zu suchen und das Modulpräfix des Typnamens auf `jl_core_module` zu setzen.

[`jl_add_standard_imports(jl_main_module)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) does "using Base" in the "Main" module.

Hinweis: `_julia_init()` setzt jetzt `jl_root_task->current_module = jl_main_module` zurück, wie es zuvor war, bevor es auf `jl_core_module` oben gesetzt wurde.

Plattform-spezifische Signalhandler werden für `SIGSEGV` (OSX, Linux) und `SIGFPE` (Windows) initialisiert.

Andere Signale (`SIGINFO, SIGBUS, SIGILL, SIGTERM, SIGABRT, SIGQUIT, SIGSYS` und `SIGPIPE`) sind mit [`sigdie_handler()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) verbunden, das einen Backtrace ausgibt.

[`jl_init_restored_module()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) ruft [`jl_module_run_initializer()`](https://github.com/JuliaLang/julia/blob/master/src/module.c) für jedes deserialisierte Modul auf, um die Funktion `__init__()` auszuführen.

Schließlich ist [`sigint_handler()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) mit `SIGINT` verbunden und ruft `jl_throw(jl_interrupt_exception)` auf.

`_julia_init()` gibt dann [back to `main()` in `cli/loader_exe.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_exe.c) zurück und `main()` ruft `repl_entrypoint(argc, (char**)argv)` auf.

!!! sidebar "sysimg"
    Wenn es eine sysimg-Datei gibt, enthält sie ein vorgefertigtes Bild der `Core`- und `Main`-Module (und alles andere, was von `boot.jl` erstellt wird). Siehe [Building the Julia system image](@ref Building-the-Julia-system-image).

    [`jl_restore_system_image()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) deserialisiert das gespeicherte sysimg in die aktuelle Julia-Laufzeitumgebung, und die Initialisierung wird nach `jl_init_box_caches()` unten fortgesetzt...

    Hinweis: [`jl_restore_system_image()` (and `staticdata.c` in general)](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) verwendet die [Legacy `ios.c` library](@ref Legacy-ios.c-library).


## `repl_entrypoint()`

[`repl_entrypoint()`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c) lädt den Inhalt von `argv[]` in [`Base.ARGS`](@ref) ein.

Wenn eine `.jl` "Programmdaten" Datei über die Befehlszeile bereitgestellt wurde, dann ruft [`exec_program()`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c) [`jl_load(program,len)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) auf, das [`jl_parse_eval_all`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) aufruft, das wiederholt [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) aufruft, um das Programm auszuführen.

However, in our example (`julia -e 'println("Hello World!")'`), [`jl_get_global(jl_base_module, jl_symbol("_start"))`](https://github.com/JuliaLang/julia/blob/master/src/module.c) looks up [`Base._start`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) and [`jl_apply()`](https://github.com/JuliaLang/julia/blob/master/src/julia.h) executes it.

## `Base._start`

[`Base._start`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) ruft [`Base.exec_options`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) auf, das [`jl_parse_input_line("println("Hello World!")")`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) aufruft, um ein Ausdrucksobjekt zu erstellen, und [`Core.eval(Main, ex)`](@ref Core.eval) um den geparsten Ausdruck `ex` im Modulkontext von `Main` auszuführen.

## `Core.eval`

[`Core.eval(Main, ex)`](@ref Core.eval) ruft [`jl_toplevel_eval_in(m, ex)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) auf, das [`jl_toplevel_eval_flex`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) aufruft. `jl_toplevel_eval_flex` implementiert eine einfache Heuristik, um zu entscheiden, ob ein gegebener Code-Thunk kompiliert oder vom Interpreter ausgeführt werden soll. Wenn `println("Hello World!")` gegeben wird, würde es normalerweise entscheiden, den Code vom Interpreter auszuführen, in diesem Fall ruft es [`jl_interpret_toplevel_thunk`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c) auf, das dann [`eval_body`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c) aufruft.

Der Stack-Dump unten zeigt, wie der Interpreter sich durch verschiedene Methoden von [`Base.println()`](@ref) und [`Base.print()`](@ref) arbeitet, bevor er bei [`write(s::IO, a::Array{T}) where T`](https://github.com/JuliaLang/julia/blob/master/base/stream.jl) ankommt, das `ccall(jl_uv_write())` ausführt.

[`jl_uv_write()`](https://github.com/JuliaLang/julia/blob/master/src/jl_uv.c) ruft `uv_write()` auf, um "Hello World!" an `JL_STDOUT` zu schreiben. Siehe [Libuv wrappers for stdio](@ref Libuv-wrappers-for-stdio).

```
Hello World!
```

| Stack frame                   | Source code     | Notes                                                |
|:----------------------------- |:--------------- |:---------------------------------------------------- |
| `jl_uv_write()`               | `jl_uv.c`       | called though [`ccall`](@ref)                        |
| `julia_write_282942`          | `stream.jl`     | function `write!(s::IO, a::Array{T}) where T`        |
| `julia_print_284639`          | `ascii.jl`      | `print(io::IO, s::String) = (write(io, s); nothing)` |
| `jlcall_print_284639`         |                 |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_trampoline()`             | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_apply_generic()`          | `gf.c`          | `Base.print(Base.TTY, String)`                       |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_trampoline()`             | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_apply_generic()`          | `gf.c`          | `Base.print(Base.TTY, String, Char, Char...)`        |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_f_apply()`                | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_trampoline()`             | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_apply_generic()`          | `gf.c`          | `Base.println(Base.TTY, String, String...)`          |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_trampoline()`             | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_apply_generic()`          | `gf.c`          | `Base.println(String,)`                              |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `do_call()`                   | `interpreter.c` |                                                      |
| `eval_body()`                 | `interpreter.c` |                                                      |
| `jl_interpret_toplevel_thunk` | `interpreter.c` |                                                      |
| `jl_toplevel_eval_flex`       | `toplevel.c`    |                                                      |
| `jl_toplevel_eval_in`         | `toplevel.c`    |                                                      |
| `Core.eval`                   | `boot.jl`       |                                                      |

Da unser Beispiel nur einen Funktionsaufruf hat, der seine Aufgabe erfüllt hat, "Hello World!" auszugeben, entfaltet sich der Stack jetzt schnell zurück zu `main()`.

## `jl_atexit_hook()`

`main()` ruft [`jl_atexit_hook()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) auf. Dies ruft `Base._atexit` auf, dann wird [`jl_gc_run_all_finalizers()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) auf und bereinigt die libuv-Handles.

## `julia_save()`

Schließlich ruft `main()` [`julia_save()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) auf, was, wenn es in der Befehlszeile angefordert wird, den Laufzeitstatus in einem neuen Systembild speichert. Siehe [`jl_compile_all()`](https://github.com/JuliaLang/julia/blob/master/src/gf.c) und [`jl_save_system_image()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c).
