# Initialization of the Julia runtime

El runtime de Julia ejecuta `julia -e 'println("Hello World!")'` de la siguiente manera:

## `main()`

La ejecución comienza en [`main()` in `cli/loader_exe.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_exe.c), que llama a `jl_load_repl()` en [`cli/loader_lib.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_lib.c), que carga algunas bibliotecas, llamando eventualmente a [`jl_repl_entrypoint()` in `src/jlapi.c`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c).

`jl_repl_entrypoint()` llama a [`libsupport_init()`](https://github.com/JuliaLang/julia/blob/master/src/support/libsupportinit.c) para establecer la configuración regional de la biblioteca C y para inicializar la biblioteca "ios" (ver [`ios_init_stdstreams()`](https://github.com/JuliaLang/julia/blob/master/src/support/ios.c) y [Legacy `ios.c` library](@ref Legacy-ios.c-library)).

A continuación, [`jl_parse_opts()`](https://github.com/JuliaLang/julia/blob/master/src/jloptions.c) se llama para procesar las opciones de la línea de comandos. Tenga en cuenta que `jl_parse_opts()` solo se ocupa de las opciones que afectan la generación de código o la inicialización temprana. Otras opciones se manejan más tarde por [`exec_options()` in `base/client.jl`](https://github.com/JuliaLang/julia/blob/master/base/client.jl).

`jl_parse_opts()` almacena las opciones de línea de comandos en el [global `jl_options` struct](https://github.com/JuliaLang/julia/blob/master/src/julia.h).

## `julia_init()`

[`julia_init()` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c) es llamado por `main()` y llama a [`_julia_init()` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c).

`_julia_init()` comienza llamando a `libsupport_init()` nuevamente (no hace nada la segunda vez).

[`restore_signals()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) se llama para poner a cero la máscara del manejador de señales.

[`jl_resolve_sysimg_location()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) busca rutas configuradas para la imagen base del sistema. Ver [Building the Julia system image](@ref Building-the-Julia-system-image).

[`jl_gc_init()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) configura grupos de asignación y listas para referencias débiles, valores preservados y finalización.

[`jl_init_frontend()`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) carga e inicializa una imagen de femtolisp precompilada que contiene el escáner/parsing.

[`jl_init_types()`](https://github.com/JuliaLang/julia/blob/master/src/jltypes.c) crea objetos de descripción de tipo `jl_datatype_t` para [built-in types defined in `julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h). p.ej.

```c
jl_any_type = jl_new_abstracttype(jl_symbol("Any"), core, NULL, jl_emptysvec);
jl_any_type->super = jl_any_type;

jl_type_type = jl_new_abstracttype(jl_symbol("Type"), core, jl_any_type, jl_emptysvec);

jl_int32_type = jl_new_primitivetype(jl_symbol("Int32"), core,
                                     jl_any_type, jl_emptysvec, 32);
```

[`jl_init_tasks()`](https://github.com/JuliaLang/julia/blob/master/src/task.c) crea el objeto `jl_datatype_t* jl_task_type`; inicializa la estructura global `jl_root_task`; y establece `jl_current_task` como la tarea raíz.

[`jl_init_codegen()`](https://github.com/JuliaLang/julia/blob/master/src/codegen.cpp) inicializa el [LLVM library](https://llvm.org).

[`jl_init_serializer()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) inicializa etiquetas de serialización de 8 bits para valores `jl_value_t` incorporados.

Si no hay un archivo sysimg (`!jl_options.image_file`), entonces se crean los módulos `Core` y `Main` y se evalúa `boot.jl`:

`jl_core_module = jl_new_module(jl_symbol("Core"))` crea el módulo `Core` de Julia.

[`jl_init_intrinsic_functions()`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp) crea un nuevo módulo de Julia `Intrinsics` que contiene símbolos constantes `jl_intrinsic_type`. Estos definen un código entero para cada [intrinsic function](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp). [`emit_intrinsic()`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp) traduce estos símbolos en instrucciones LLVM durante la generación de código.

[`jl_init_primitives()`](https://github.com/JuliaLang/julia/blob/master/src/builtins.c) conecta funciones C a símbolos de funciones de Julia. Por ejemplo, el símbolo `Core.:(===)()` está vinculado al puntero de función C `jl_f_is()` al llamar a `add_builtin_func("===", jl_f_is)`.

[`jl_new_main_module()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) crea el módulo global "Main" y establece `jl_current_task->current_module = jl_main_module`.

Nota: `_julia_init()` [then sets](https://github.com/JuliaLang/julia/blob/master/src/init.c) `jl_root_task->current_module = jl_core_module`. `jl_root_task` es un alias de `jl_current_task` en este punto, por lo que el `current_module` establecido por `jl_new_main_module()` arriba es sobrescrito.

[`jl_load("boot.jl", sizeof("boot.jl"))`](https://github.com/JuliaLang/julia/blob/master/src/init.c) llama a [`jl_parse_eval_all`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) que llama repetidamente a [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) para ejecutar [`boot.jl`](https://github.com/JuliaLang/julia/blob/master/base/boot.jl). <!– TODO – profundizar en eval? –>

[`jl_get_builtin_hooks()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) inicializa punteros globales de C a globales de Julia definidos en `boot.jl`.

[`jl_init_box_caches()`](https://github.com/JuliaLang/julia/blob/master/src/datatype.c) pre-asigna objetos de valor entero global en caja para valores de hasta 1024. Esto acelera la asignación de enteros en caja más adelante. p.ej.:

```c
jl_value_t *jl_box_uint8(uint32_t x)
{
    return boxed_uint8_cache[(uint8_t)x];
}
```

[`_julia_init()` iterates](https://github.com/JuliaLang/julia/blob/master/src/init.c) sobre el `jl_core_module->bindings.table` buscando valores de `jl_datatype_t` y establece el prefijo del nombre del tipo en el módulo `jl_core_module`.

[`jl_add_standard_imports(jl_main_module)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) hace "uso de Base" en el módulo "Principal".

Nota: `_julia_init()` ahora revierte a `jl_root_task->current_module = jl_main_module` como lo era antes de ser establecido en `jl_core_module` arriba.

Los controladores de señales específicos de la plataforma se inicializan para `SIGSEGV` (OSX, Linux) y `SIGFPE` (Windows).

Otros señales (`SIGINFO, SIGBUS, SIGILL, SIGTERM, SIGABRT, SIGQUIT, SIGSYS` y `SIGPIPE`) están conectadas a [`sigdie_handler()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) que imprime un backtrace.

[`jl_init_restored_module()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) llama a [`jl_module_run_initializer()`](https://github.com/JuliaLang/julia/blob/master/src/module.c) para cada módulo deserializado para ejecutar la función `__init__()`.

Finalmente [`sigint_handler()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) está conectado a `SIGINT` y llama a `jl_throw(jl_interrupt_exception)`.

`_julia_init()` luego devuelve [back to `main()` in `cli/loader_exe.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_exe.c) y `main()` llama a `repl_entrypoint(argc, (char**)argv)`.

!!! sidebar "sysimg"
    Si hay un archivo sysimg, contiene una imagen pre-cocinada de los módulos `Core` y `Main` (y cualquier otra cosa que sea creada por `boot.jl`). Consulta [Building the Julia system image](@ref Building-the-Julia-system-image).

    [`jl_restore_system_image()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) deserializa la imagen del sistema guardada en el entorno de ejecución actual de Julia y la inicialización continúa después de `jl_init_box_caches()` a continuación...

    Nota: [`jl_restore_system_image()` (and `staticdata.c` in general)](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) utiliza el [Legacy `ios.c` library](@ref Legacy-ios.c-library).


## `repl_entrypoint()`

[`repl_entrypoint()`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c) carga el contenido de `argv[]` en [`Base.ARGS`](@ref).

Si se suministró un archivo de "programa" `.jl` en la línea de comandos, entonces [`exec_program()`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c) llama a [`jl_load(program,len)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) que llama a [`jl_parse_eval_all`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) que llama repetidamente a [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) para ejecutar el programa.

However, in our example (`julia -e 'println("Hello World!")'`), [`jl_get_global(jl_base_module, jl_symbol("_start"))`](https://github.com/JuliaLang/julia/blob/master/src/module.c) looks up [`Base._start`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) and [`jl_apply()`](https://github.com/JuliaLang/julia/blob/master/src/julia.h) executes it.

## `Base._start`

[`Base._start`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) llama [`Base.exec_options`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) que llama [`jl_parse_input_line("println("Hello World!")")`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) para crear un objeto de expresión y [`Core.eval(Main, ex)`](@ref Core.eval) para ejecutar la expresión analizada `ex` en el contexto del módulo de `Main`.

## `Core.eval`

[`Core.eval(Main, ex)`](@ref Core.eval) llama a [`jl_toplevel_eval_in(m, ex)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c), que llama a [`jl_toplevel_eval_flex`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c). `jl_toplevel_eval_flex` implementa una heurística simple para decidir si compilar un código dado o ejecutarlo mediante un intérprete. Cuando se le da `println("Hello World!")`, generalmente decidiría ejecutar el código mediante el intérprete, en cuyo caso llama a [`jl_interpret_toplevel_thunk`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c), que luego llama a [`eval_body`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c).

El volcado de pila a continuación muestra cómo el intérprete trabaja a través de varios métodos de [`Base.println()`](@ref) y [`Base.print()`](@ref) antes de llegar a [`write(s::IO, a::Array{T}) where T`](https://github.com/JuliaLang/julia/blob/master/base/stream.jl) que hace `ccall(jl_uv_write())`.

[`jl_uv_write()`](https://github.com/JuliaLang/julia/blob/master/src/jl_uv.c) llama a `uv_write()` para escribir "¡Hola Mundo!" en `JL_STDOUT`. Ver [Libuv wrappers for stdio](@ref Libuv-wrappers-for-stdio).

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

Dado que nuestro ejemplo tiene solo una llamada a la función, que ha cumplido su tarea de imprimir "¡Hola Mundo!", la pila ahora se desenrolla rápidamente de vuelta a `main()`.

## `jl_atexit_hook()`

`main()` llama a [`jl_atexit_hook()`](https://github.com/JuliaLang/julia/blob/master/src/init.c). Esto llama a `Base._atexit`, luego llama a [`jl_gc_run_all_finalizers()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) y limpia los manejadores de libuv.

## `julia_save()`

Finalmente, `main()` llama a [`julia_save()`](https://github.com/JuliaLang/julia/blob/master/src/init.c), que si se solicita en la línea de comandos, guarda el estado de ejecución en una nueva imagen del sistema. Consulta [`jl_compile_all()`](https://github.com/JuliaLang/julia/blob/master/src/gf.c) y [`jl_save_system_image()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c).
