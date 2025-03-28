# Initialization of the Julia runtime

Comment le runtime Julia exécute `julia -e 'println("Hello World!")'` ?

## `main()`

L'exécution commence à [`main()` in `cli/loader_exe.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_exe.c), qui appelle `jl_load_repl()` dans [`cli/loader_lib.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_lib.c), qui charge quelques bibliothèques, appelant finalement [`jl_repl_entrypoint()` in `src/jlapi.c`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c).

`jl_repl_entrypoint()` appelle [`libsupport_init()`](https://github.com/JuliaLang/julia/blob/master/src/support/libsupportinit.c) pour définir la locale de la bibliothèque C et pour initialiser la bibliothèque "ios" (voir [`ios_init_stdstreams()`](https://github.com/JuliaLang/julia/blob/master/src/support/ios.c) et [Legacy `ios.c` library](@ref Legacy-ios.c-library)).

Le prochain [`jl_parse_opts()`](https://github.com/JuliaLang/julia/blob/master/src/jloptions.c) est appelé pour traiter les options de ligne de commande. Notez que `jl_parse_opts()` ne s'occupe que des options qui affectent la génération de code ou l'initialisation précoce. D'autres options sont traitées plus tard par [`exec_options()` in `base/client.jl`](https://github.com/JuliaLang/julia/blob/master/base/client.jl).

`jl_parse_opts()` stocke les options de ligne de commande dans le [global `jl_options` struct](https://github.com/JuliaLang/julia/blob/master/src/julia.h).

## `julia_init()`

[`julia_init()` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c) est appelé par `main()` et appelle [`_julia_init()` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c).

`_julia_init()` commence par appeler `libsupport_init()` à nouveau (il ne fait rien la deuxième fois).

[`restore_signals()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) est appelé pour annuler le masque du gestionnaire de signal.

[`jl_resolve_sysimg_location()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) recherche les chemins configurés pour l'image système de base. Voir [Building the Julia system image](@ref Building-the-Julia-system-image).

[`jl_gc_init()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) configure des pools d'allocation et des listes pour les références faibles, les valeurs préservées et la finalisation.

[`jl_init_frontend()`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) charge et initialise une image femtolisp précompilée contenant le scanner/parser.

[`jl_init_types()`](https://github.com/JuliaLang/julia/blob/master/src/jltypes.c) crée des objets de description de type `jl_datatype_t` pour le [built-in types defined in `julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h). par exemple.

```c
jl_any_type = jl_new_abstracttype(jl_symbol("Any"), core, NULL, jl_emptysvec);
jl_any_type->super = jl_any_type;

jl_type_type = jl_new_abstracttype(jl_symbol("Type"), core, jl_any_type, jl_emptysvec);

jl_int32_type = jl_new_primitivetype(jl_symbol("Int32"), core,
                                     jl_any_type, jl_emptysvec, 32);
```

[`jl_init_tasks()`](https://github.com/JuliaLang/julia/blob/master/src/task.c) crée l'objet `jl_datatype_t* jl_task_type` ; initialise la structure globale `jl_root_task` ; et définit `jl_current_task` comme la tâche racine.

[`jl_init_codegen()`](https://github.com/JuliaLang/julia/blob/master/src/codegen.cpp) initialise le [LLVM library](https://llvm.org).

[`jl_init_serializer()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) initialise les balises de sérialisation 8 bits pour les valeurs `jl_value_t` intégrées.

S'il n'y a pas de fichier sysimg (`!jl_options.image_file`), alors les modules `Core` et `Main` sont créés et `boot.jl` est évalué :

`jl_core_module = jl_new_module(jl_symbol("Core"))` crée le module `Core` de Julia.

[`jl_init_intrinsic_functions()`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp) crée un nouveau module Julia `Intrinsics` contenant des symboles constants `jl_intrinsic_type`. Ceux-ci définissent un code entier pour chaque [intrinsic function](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp). [`emit_intrinsic()`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp) traduit ces symboles en instructions LLVM lors de la génération de code.

[`jl_init_primitives()`](https://github.com/JuliaLang/julia/blob/master/src/builtins.c) connecte les fonctions C aux symboles de fonction Julia. Par exemple, le symbole `Core.:(===)()` est lié au pointeur de fonction C `jl_f_is()` en appelant `add_builtin_func("===", jl_f_is)`.

[`jl_new_main_module()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) crée le module global "Main" et définit `jl_current_task->current_module = jl_main_module`.

Note : `_julia_init()` [then sets](https://github.com/JuliaLang/julia/blob/master/src/init.c) `jl_root_task->current_module = jl_core_module`. `jl_root_task` est un alias de `jl_current_task` à ce stade, donc le `current_module` défini par `jl_new_main_module()` ci-dessus est écrasé.

[`jl_load("boot.jl", sizeof("boot.jl"))`](https://github.com/JuliaLang/julia/blob/master/src/init.c) appelle [`jl_parse_eval_all`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) qui appelle à plusieurs reprises [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) pour exécuter [`boot.jl`](https://github.com/JuliaLang/julia/blob/master/base/boot.jl). <!– TODO – approfondir dans eval? –>

[`jl_get_builtin_hooks()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) initialise des pointeurs C globaux vers des globals Julia définis dans `boot.jl`.

[`jl_init_box_caches()`](https://github.com/JuliaLang/julia/blob/master/src/datatype.c) pré-alloue des objets de valeur entier global encapsulés pour des valeurs allant jusqu'à 1024. Cela accélère l'allocation d'entiers encapsulés par la suite. par exemple :

```c
jl_value_t *jl_box_uint8(uint32_t x)
{
    return boxed_uint8_cache[(uint8_t)x];
}
```

[`_julia_init()` iterates](https://github.com/JuliaLang/julia/blob/master/src/init.c) sur le `jl_core_module->bindings.table` à la recherche de valeurs `jl_datatype_t` et définit le préfixe de module du nom de type sur `jl_core_module`.

[`jl_add_standard_imports(jl_main_module)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) utilise "Base" dans le module "Main".

Remarque : `_julia_init()` revient maintenant à `jl_root_task->current_module = jl_main_module` comme c'était le cas avant d'être défini sur `jl_core_module` ci-dessus.

Des gestionnaires de signaux spécifiques à la plateforme sont initialisés pour `SIGSEGV` (OSX, Linux) et `SIGFPE` (Windows).

D'autres signaux (`SIGINFO, SIGBUS, SIGILL, SIGTERM, SIGABRT, SIGQUIT, SIGSYS` et `SIGPIPE`) sont connectés à [`sigdie_handler()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) qui imprime une trace de pile.

[`jl_init_restored_module()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) appelle [`jl_module_run_initializer()`](https://github.com/JuliaLang/julia/blob/master/src/module.c) pour chaque module désérialisé afin d'exécuter la fonction `__init__()`.

Enfin, [`sigint_handler()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) est connecté à `SIGINT` et appelle `jl_throw(jl_interrupt_exception)`.

`_julia_init()` renvoie alors [back to `main()` in `cli/loader_exe.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_exe.c) et `main()` appelle `repl_entrypoint(argc, (char**)argv)`.

!!! sidebar "sysimg"
    S'il y a un fichier sysimg, il contient une image pré-cuite des modules `Core` et `Main` (et tout ce qui est créé par `boot.jl`). Voir [Building the Julia system image](@ref Building-the-Julia-system-image).

    [`jl_restore_system_image()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) désérialise l'image système sauvegardée dans l'environnement d'exécution Julia actuel et l'initialisation se poursuit après `jl_init_box_caches()` ci-dessous...

    Note : [`jl_restore_system_image()` (and `staticdata.c` in general)](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) utilise le [Legacy `ios.c` library](@ref Legacy-ios.c-library).


## `repl_entrypoint()`

[`repl_entrypoint()`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c) charge le contenu de `argv[]` dans [`Base.ARGS`](@ref).

Si un fichier "programme" `.jl` est fourni en ligne de commande, alors [`exec_program()`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c) appelle [`jl_load(program,len)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) qui appelle [`jl_parse_eval_all`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) qui appelle à plusieurs reprises [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) pour exécuter le programme.

However, in our example (`julia -e 'println("Hello World!")'`), [`jl_get_global(jl_base_module, jl_symbol("_start"))`](https://github.com/JuliaLang/julia/blob/master/src/module.c) looks up [`Base._start`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) and [`jl_apply()`](https://github.com/JuliaLang/julia/blob/master/src/julia.h) executes it.

## `Base._start`

[`Base._start`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) appelle [`Base.exec_options`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) qui appelle [`jl_parse_input_line("println("Hello World!")")`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) pour créer un objet d'expression et [`Core.eval(Main, ex)`](@ref Core.eval) pour exécuter l'expression analysée `ex` dans le contexte du module `Main`.

## `Core.eval`

[`Core.eval(Main, ex)`](@ref Core.eval) appelle [`jl_toplevel_eval_in(m, ex)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c), qui appelle [`jl_toplevel_eval_flex`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c). `jl_toplevel_eval_flex` implémente une heuristique simple pour décider s'il faut compiler un code donné ou l'exécuter par interpréteur. Lorsqu'on lui donne `println("Hello World!")`, il déciderait généralement d'exécuter le code par interpréteur, auquel cas il appelle [`jl_interpret_toplevel_thunk`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c), qui appelle ensuite [`eval_body`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c).

L'exception de pile ci-dessous montre comment l'interpréteur parcourt diverses méthodes de [`Base.println()`](@ref) et [`Base.print()`](@ref) avant d'arriver à [`write(s::IO, a::Array{T}) where T`](https://github.com/JuliaLang/julia/blob/master/base/stream.jl) qui fait `ccall(jl_uv_write())`.

[`jl_uv_write()`](https://github.com/JuliaLang/julia/blob/master/src/jl_uv.c) appelle `uv_write()` pour écrire "Hello World!" sur `JL_STDOUT`. Voir [Libuv wrappers for stdio](@ref Libuv-wrappers-for-stdio).

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

Puisque notre exemple n'a qu'un seul appel de fonction, qui a accompli sa tâche d'imprimer "Hello World !", la pile se déroule rapidement de nouveau vers `main()`.

## `jl_atexit_hook()`

`main()` appelle [`jl_atexit_hook()`](https://github.com/JuliaLang/julia/blob/master/src/init.c). Cela appelle `Base._atexit`, puis appelle [`jl_gc_run_all_finalizers()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) et nettoie les poignées libuv.

## `julia_save()`

Enfin, `main()` appelle [`julia_save()`](https://github.com/JuliaLang/julia/blob/master/src/init.c), qui, si demandé en ligne de commande, enregistre l'état d'exécution dans une nouvelle image système. Voir [`jl_compile_all()`](https://github.com/JuliaLang/julia/blob/master/src/gf.c) et [`jl_save_system_image()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c).
