# [gdb debugging tips](@id gdb-debugging-tips)

## Displaying Julia variables

Dentro de `gdb`, cualquier objeto `jl_value_t*` `obj` se puede mostrar usando

```
(gdb) call jl_(obj)
```

El objeto se mostrará en la sesión de `julia`, no en la sesión de gdb. Esta es una forma útil de descubrir los tipos y valores de los objetos que están siendo manipulados por el código C de Julia.

De manera similar, si estás depurando algunos de los internos de Julia (por ejemplo, `compiler.jl`), puedes imprimir `obj` usando

```julia
ccall(:jl_, Cvoid, (Any,), obj)
```

Esta es una buena manera de eludir los problemas que surgen del orden en que se inicializan los flujos de salida de Julia.

El intérprete flisp de Julia utiliza objetos `value_t`; estos se pueden mostrar con `call fl_print(fl_ctx, ios_stdout, obj)`.

## Useful Julia variables for Inspecting

Mientras que las direcciones de muchas variables, como los singletons, pueden ser útiles para imprimir en muchos fallos, hay un número de variables adicionales (ver `julia.h` para una lista completa) que son aún más útiles.

  * (cuando en `jl_apply_generic`) `mfunc` y `jl_uncompress_ast(mfunc->def, mfunc->code)` :: para averiguar un poco sobre la pila de llamadas
  * `jl_lineno` y `jl_filename` :: para averiguar desde qué línea en una prueba comenzar a depurar (o determinar cuán lejos se ha analizado en un archivo)
  * `$1` :: no es realmente una variable, pero sigue siendo una abreviatura útil para referirse al resultado del último comando de gdb (como `print`)
  * `jl_options` :: a veces útil, ya que enumera todas las opciones de línea de comandos que se analizaron con éxito
  * `jl_uv_stderr` :: porque a quién no le gusta poder interactuar con stdio

## Useful Julia functions for Inspecting those variables

  * `jl_print_task_backtraces(0)` :: Similar a `thread apply all bt` de gdb o `thread backtrace all` de lldb. Ejecuta todos los hilos mientras imprime las trazas de pila para todas las tareas existentes.
  * `jl_gdblookup($pc)` :: Para buscar la función y línea actuales.
  * `jl_gdblookupinfo($pc)` :: Para buscar el objeto de instancia del método actual.
  * `jl_gdbdumpcode(mi)` :: Para volcar todo el `code_typed/code_llvm/code_asm` cuando el REPL no está funcionando correctamente.
  * `jlbacktrace()` :: Para volcar la pila de retroceso actual de Julia en stderr. Solo utilizable después de que se haya llamado a `record_backtrace()`.
  * `jl_dump_llvm_value(Value*)` :: Para invocar `Value->dump()` en gdb, donde no funciona de forma nativa. Por ejemplo, `f->linfo->functionObject`, `f->linfo->specFunctionObject`, y `to_function(f->linfo)`.
  * `jl_dump_llvm_module(Module*)` :: Para invocar `Module->dump()` en gdb, donde no funciona de forma nativa.
  * `Type->dump()` :: solo funciona en lldb. Nota: añade algo como `;1` para evitar que lldb imprima su aviso sobre la salida.
  * `jl_eval_string("expr")` :: para invocar efectos secundarios para modificar el estado actual o para buscar símbolos
  * `jl_typeof(jl_value_t*)` :: para extraer la etiqueta de tipo de un valor de Julia (en gdb, llama a `macro define jl_typeof jl_typeof` primero, o elige algo corto como `ty` para el primer argumento para definir un atajo)

## Inserting breakpoints for inspection from gdb

En tu sesión de `gdb`, establece un punto de interrupción en `jl_breakpoint` de la siguiente manera:

```
(gdb) break jl_breakpoint
```

Luego, dentro de tu código Julia, inserta una llamada a `jl_breakpoint` añadiendo

```julia
ccall(:jl_breakpoint, Cvoid, (Any,), obj)
```

donde `obj` puede ser cualquier variable o tupla que desees que sea accesible en el punto de interrupción.

Es particularmente útil retroceder al marco `jl_apply`, desde el cual puedes mostrar los argumentos de una función usando, por ejemplo,

```
(gdb) call jl_(args[0])
```

Otro marco útil es `to_function(jl_method_instance_t *li, bool cstyle)`. El argumento `jl_method_instance_t*` es una estructura con una referencia al AST final enviado al compilador. Sin embargo, el AST en este punto generalmente estará comprimido; para ver el AST, llama a `jl_uncompress_ast` y luego pasa el resultado a `jl_`:

```
#2  0x00007ffff7928bf7 in to_function (li=0x2812060, cstyle=false) at codegen.cpp:584
584          abort();
(gdb) p jl_(jl_uncompress_ast(li, li->ast))
```

## Inserting breakpoints upon certain conditions

### Loading a particular file

Supongamos que el archivo es `sysimg.jl`:

```
(gdb) break jl_load if strcmp(fname, "sysimg.jl")==0
```

### Calling a particular method

```
(gdb) break jl_apply_generic if strcmp((char*)(jl_symbol_name)(jl_gf_mtable(F)->name), "method_to_break")==0
```

Dado que esta función se utiliza para cada llamada, harás que todo sea 1000 veces más lento si haces esto.

## Dealing with signals

Julia requiere algunas señales para funcionar correctamente. El perfilador utiliza `SIGUSR2` para muestreo y el recolector de basura utiliza `SIGSEGV` para la sincronización de hilos. Si estás depurando algún código que utiliza el perfilador o múltiples hilos, es posible que desees permitir que el depurador ignore estas señales, ya que pueden ser activadas con mucha frecuencia durante las operaciones normales. El comando para hacer esto en GDB es (reemplaza `SIGSEGV` con `SIGUSR2` u otras señales que desees ignorar):

```
(gdb) handle SIGSEGV noprint nostop pass
```

El comando LLDB correspondiente es (después de que el proceso se haya iniciado):

```
(lldb) pro hand -p true -s false -n false SIGSEGV
```

Si estás depurando un segfault con código multihilo, puedes establecer un punto de interrupción en `jl_critical_error` (`sigdie_handler` también debería funcionar en Linux y BSD) para capturar solo el segfault real en lugar de los puntos de sincronización del GC.

## Debugging during Julia's build process (bootstrap)

Los errores que ocurren durante `make` necesitan un manejo especial. Julia se construye en dos etapas, construyendo `sys0` y `sys.ji`. Para ver qué comandos se están ejecutando en el momento de la falla, usa `make VERBOSE=1`.

En el momento de escribir esto, puedes depurar errores de compilación durante la fase `sys0` desde el directorio `base` utilizando:

```
julia/base$ gdb --args ../usr/bin/julia-debug -C native --build ../usr/lib/julia/sys0 sysimg.jl
```

Es posible que necesites eliminar todos los archivos en `usr/lib/julia/` para que esto funcione.

Puedes depurar la fase `sys.ji` usando:

```
julia/base$ gdb --args ../usr/bin/julia-debug -C native --build ../usr/lib/julia/sys -J ../usr/lib/julia/sys0.ji sysimg.jl
```

Por defecto, cualquier error hará que Julia salga, incluso bajo gdb. Para capturar un error "en el acto", establece un punto de interrupción en `jl_error` (hay varios otros lugares útiles, para tipos específicos de fallos, incluyendo: `jl_too_few_args`, `jl_too_many_args` y `jl_throw`).

Una vez que se captura un error, una técnica útil es recorrer la pila y examinar la función inspeccionando la llamada relacionada a `jl_apply`. Para tomar un ejemplo del mundo real:

```
Breakpoint 1, jl_throw (e=0x7ffdf42de400) at task.c:802
802 {
(gdb) p jl_(e)
ErrorException("auto_unbox: unable to determine argument type")
$2 = void
(gdb) bt 10
#0  jl_throw (e=0x7ffdf42de400) at task.c:802
#1  0x00007ffff65412fe in jl_error (str=0x7ffde56be000 <_j_str267> "auto_unbox:
   unable to determine argument type")
   at builtins.c:39
#2  0x00007ffde56bd01a in julia_convert_16886 ()
#3  0x00007ffff6541154 in jl_apply (f=0x7ffdf367f630, args=0x7fffffffc2b0, nargs=2) at julia.h:1281
...
```

El `jl_apply` más reciente está en el marco #3, así que podemos volver allí y mirar el AST para la función `julia_convert_16886`. Este es el nombre único para algún método de `convert`. `f` en este marco es un `jl_function_t*`, así que podemos mirar la firma de tipo, si la hay, desde el campo `specTypes`:

```
(gdb) f 3
#3  0x00007ffff6541154 in jl_apply (f=0x7ffdf367f630, args=0x7fffffffc2b0, nargs=2) at julia.h:1281
1281            return f->fptr((jl_value_t*)f, args, nargs);
(gdb) p f->linfo->specTypes
$4 = (jl_tupletype_t *) 0x7ffdf39b1030
(gdb) p jl_( f->linfo->specTypes )
Tuple{Type{Float32}, Float64}           # <-- type signature for julia_convert_16886
```

Entonces, podemos mirar el AST para esta función:

```
(gdb) p jl_( jl_uncompress_ast(f->linfo, f->linfo->ast) )
Expr(:lambda, Array{Any, 1}[:#s29, :x], Array{Any, 1}[Array{Any, 1}[], Array{Any, 1}[Array{Any, 1}[:#s29, :Any, 0], Array{Any, 1}[:x, :Any, 0]], Array{Any, 1}[], 0], Expr(:body,
Expr(:line, 90, :float.jl)::Any,
Expr(:return, Expr(:call, :box, :Float32, Expr(:call, :fptrunc, :Float32, :x)::Any)::Any)::Any)::Any)::Any
```

Finalmente, y quizás de manera más útil, podemos forzar la recompilación de la función para poder recorrer el proceso de generación de código. Para hacer esto, borra el `functionObject` en caché del `jl_lamdbda_info_t*`:

```
(gdb) p f->linfo->functionObject
$8 = (void *) 0x1289d070
(gdb) set f->linfo->functionObject = NULL
```

Luego, establece un punto de interrupción en algún lugar útil (por ejemplo, `emit_function`, `emit_expr`, `emit_call`, etc.) y ejecuta la generación de código:

```
(gdb) p jl_compile(f)
... # your breakpoint here
```

## Debugging precompilation errors

La precompilación de módulos genera un proceso de Julia separado para precompilar cada módulo. Establecer un punto de interrupción o capturar fallos en un trabajador de precompilación requiere adjuntar un depurador al trabajador. El enfoque más fácil es configurar el depurador para vigilar los nuevos lanzamientos de procesos que coincidan con un nombre dado. Por ejemplo:

```
(gdb) attach -w -n julia-debug
```

o:

```
(lldb) process attach -w -n julia-debug
```

Luego ejecuta un script/comando para iniciar la precompilación. Como se describió anteriormente, utiliza puntos de interrupción condicionales en el proceso principal para capturar eventos específicos de carga de archivos y reducir la ventana de depuración. (algunos sistemas operativos pueden requerir enfoques alternativos, como seguir cada `fork` desde el proceso principal)

## Mozilla's Record and Replay Framework (rr)

Julia ahora funciona directamente con [rr](https://rr-project.org/), el marco de grabación ligero y depuración determinista de Mozilla. Esto te permite reproducir el rastro de una ejecución de manera determinista. Los espacios de direcciones, contenidos de registros, datos de llamadas al sistema, etc., de la ejecución reproducida son exactamente los mismos en cada ejecución.

Se requiere una versión reciente de rr (3.1.0 o superior).

### Reproducing concurrency bugs with rr

rr simula una máquina de un solo hilo por defecto. Para depurar código concurrente, puedes usar `rr record --chaos`, lo que hará que rr simule entre uno y ocho núcleos, elegidos al azar. Por lo tanto, es posible que desees establecer `JULIA_NUM_THREADS=8` y volver a ejecutar tu código bajo rr hasta que hayas atrapado tu error.
