# Eval of Julia code

Una de las partes más difíciles de aprender cómo el lenguaje Julia ejecuta código es entender cómo todas las piezas trabajan juntas para ejecutar un bloque de código.

Cada fragmento de código típicamente pasa por muchos pasos con nombres potencialmente desconocidos, tales como (sin un orden particular): flisp, AST, C++, LLVM, `eval`, `typeinf`, `macroexpand`, sysimg (o imagen del sistema), arranque, compilar, analizar, ejecutar, JIT, interpretar, empaquetar, desempaquetar, función intrínseca y función primitiva, antes de convertirse en el resultado deseado (con suerte).

!!! sidebar "Definitions"
      * REPL

        REPL significa Read-Eval-Print Loop. Es simplemente lo que llamamos al entorno de línea de comandos para abreviar.
      * AST

        Árbol de Sintaxis Abstracto El AST es la representación digital de la estructura del código. En esta forma, el código ha sido tokenizado por su significado para que sea más adecuado para la manipulación y ejecución.


![Diagrama del flujo del compilador](./img/compiler_diagram.png)

## Julia Execution

La vista de 10,000 pies de todo el proceso es la siguiente:

1. El usuario inicia `julia`.
2. La función C `main()` de `cli/loader_exe.c` se llama. Esta función procesa los argumentos de la línea de comandos, llenando la estructura `jl_options` y configurando la variable `ARGS`. Luego inicializa Julia (llamando a [`julia_init` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c), que puede cargar un [sysimg](@ref dev-sysimg) previamente compilado. Finalmente, pasa el control a Julia llamando a [`Base._start()`](https://github.com/JuliaLang/julia/blob/master/base/client.jl).
3. Cuando `_start()` toma el control, la secuencia subsiguiente de comandos depende de los argumentos de la línea de comandos proporcionados. Por ejemplo, si se suministró un nombre de archivo, procederá a ejecutar ese archivo. De lo contrario, comenzará un REPL interactivo.
4. Omitiendo los detalles sobre cómo el REPL interactúa con el usuario, digamos simplemente que el programa termina con un bloque de código que desea ejecutar.
5. Si el bloque de código a ejecutar está en un archivo, [`jl_load(char *filename)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) se invoca para cargar el archivo y [parse](@ref dev-parsing) lo. Cada fragmento de código se pasa luego a `eval` para ejecutarlo.
6. Cada fragmento de código (o AST) se entrega a [`eval()`](@ref) para convertirlo en resultados.
7. [`eval()`](@ref) toma cada fragmento de código e intenta ejecutarlo en [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c).
8. `jl_toplevel_eval_flex()` decide si el código es una acción "toplevel" (como `using` o `module`), lo cual sería inválido dentro de una función. Si es así, pasa el código al intérprete de nivel superior.
9. `jl_toplevel_eval_flex()` luego [expands](@ref dev-macro-expansion) el código para eliminar cualquier macro y "bajar" el AST para hacerlo más simple de ejecutar.
10. `jl_toplevel_eval_flex()` luego utiliza algunas heurísticas simples para decidir si compilar JIT el AST o interpretarlo directamente.
11. La mayor parte del trabajo para interpretar el código es manejado por [`eval` in `interpreter.c`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c).
12. Si en su lugar, el código se compila, la mayor parte del trabajo es manejado por `codegen.cpp`. Cada vez que se llama a una función de Julia por primera vez con un conjunto dado de tipos de argumentos, [type inference](@ref dev-type-inference) se ejecutará en esa función. Esta información es utilizada por el paso [codegen](@ref dev-codegen) para generar código más rápido.
13. Eventualmente, el usuario sale del REPL, o se alcanza el final del programa, y el método `_start()` devuelve.
14. Justo antes de salir, `main()` llama a [`jl_atexit_hook(exit_code)`](https://github.com/JuliaLang/julia/blob/master/src/init.c). Esto llama a `Base._atexit()` (que llama a cualquier función registrada en [`atexit()`](@ref) dentro de Julia). Luego llama a [`jl_gc_run_all_finalizers()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c). Finalmente, limpia de manera ordenada todos los manejadores de `libuv` y espera a que se vacíen y cierren.

## [Parsing](@id dev-parsing)

El analizador de Julia es un pequeño programa lisp escrito en femtolisp, cuyo código fuente se distribuye dentro de Julia en [src/flisp](https://github.com/JuliaLang/julia/tree/master/src/flisp).

Las funciones de interfaz para esto están definidas principalmente en [`jlfrontend.scm`](https://github.com/JuliaLang/julia/blob/master/src/jlfrontend.scm). El código en [`ast.c`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) maneja esta transferencia en el lado de Julia.

Los otros archivos relevantes en esta etapa son [`julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm), que maneja la tokenización del código Julia y lo convierte en un AST, y [`julia-syntax.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-syntax.scm), que se encarga de transformar representaciones complejas de AST en representaciones de AST más simples y "reducidas" que son más adecuadas para el análisis y la ejecución.

Si deseas probar el analizador sin reconstruir Julia en su totalidad, puedes ejecutar el frontend por su cuenta de la siguiente manera:

```
$ cd src
$ flisp/flisp
> (load "jlfrontend.scm")
> (jl-parse-file "<filename>")
```

## [Macro Expansion](@id dev-macro-expansion)

Cuando [`eval()`](@ref) encuentra un macro, expande ese nodo AST antes de intentar evaluar la expresión. La expansión de macros implica una transferencia desde `4d61726b646f776e2e436f64652822222c20226576616c28292229_40726566` (en Julia), a la función de análisis `jl_macroexpand()` (escrita en `flisp`) al macro de Julia en sí (escrito en - qué más - Julia) a través de `fl_invoke_julia_macro()`, y de vuelta.

Típicamente, la expansión de macros se invoca como un primer paso durante una llamada a [`Meta.lower()`](@ref)/`jl_expand()`, aunque también se puede invocar directamente mediante una llamada a [`macroexpand()`](@ref)/`jl_macroexpand()`.

## [Type Inference](@id dev-type-inference)

La inferencia de tipos se implementa en Julia mediante [`typeinf()` in `compiler/typeinfer.jl`](https://github.com/JuliaLang/julia/blob/master/base/compiler/typeinfer.jl). La inferencia de tipos es el proceso de examinar una función de Julia y determinar los límites para los tipos de cada una de sus variables, así como los límites sobre el tipo del valor de retorno de la función. Esto permite muchas optimizaciones futuras, como el desboxing de valores inmutables conocidos y la elevación en tiempo de compilación de varias operaciones en tiempo de ejecución, como el cálculo de desplazamientos de campos y punteros de función. La inferencia de tipos también puede incluir otros pasos, como la propagación de constantes y la inlining.

!!! sidebar "More Definitions"
      * JIT

        Compilación Justo a Tiempo El proceso de generar código de máquina nativo en memoria justo cuando se necesita.
      * LLVM

        Máquina Virtual de Bajo Nivel (un compilador) El compilador JIT de Julia es un programa/biblioteca llamado libLLVM. La generación de código en Julia se refiere tanto al proceso de tomar un AST de Julia y convertirlo en instrucciones LLVM, como al proceso de optimización de LLVM y su conversión en instrucciones de ensamblador nativo.
      * C++

        El lenguaje de programación en el que está implementado LLVM, lo que significa que la generación de código también está implementada en este lenguaje. El resto de la biblioteca de Julia está implementado en C, en parte porque su conjunto de características más pequeño lo hace más utilizable como una capa de interfaz entre lenguajes.
      * caja

        Este término se utiliza para describir el proceso de tomar un valor y asignar un envoltorio alrededor de los datos que son rastreados por el recolector de basura (gc) y están etiquetados con el tipo del objeto.
      * desempaquetar

        La inversión de encerrar un valor. Esta operación permite una manipulación más eficiente de los datos cuando el tipo de esos datos se conoce completamente en tiempo de compilación (a través de la inferencia de tipos).
      * función genérica

        Una función de Julia compuesta por múltiples "métodos" que se seleccionan para la dispatch dinámica en función de la firma de tipo de argumento.
      * función anónima o "método"

        Una función de Julia sin nombre y sin capacidades de despacho de tipos
      * función primitiva

        Una función implementada en C pero expuesta en Julia como una función nombrada "método" (aunque sin capacidades de despacho de funciones genéricas, similar a una función anónima)
      * función intrínseca

        Una operación de bajo nivel expuesta como una función en Julia. Estas pseudo-funciones implementan operaciones sobre bits en bruto, como la suma y la extensión de signo, que no se pueden expresar directamente de ninguna otra manera. Dado que operan directamente sobre los bits, deben ser compiladas en una función y rodeadas por una llamada a `Core.Intrinsics.box(T, ...)` para reasignar la información de tipo al valor.


## [JIT Code Generation](@id dev-codegen)

Codegen es el proceso de convertir un AST de Julia en código de máquina nativo.

El entorno JIT se inicializa mediante una llamada temprana a [`jl_init_codegen` in `codegen.cpp`](https://github.com/JuliaLang/julia/blob/master/src/codegen.cpp).

A demanda, un método de Julia se convierte en una función nativa mediante la función `emit_function(jl_method_instance_t*)`. (nota, al usar el MCJIT (en LLVM v3.4+), cada función debe ser JIT en un nuevo módulo). Esta función llama recursivamente a `emit_expr()` hasta que toda la función ha sido emitida.

Gran parte del resto de este archivo está dedicado a varias optimizaciones manuales de patrones de código específicos. Por ejemplo, `emit_known_call()` sabe cómo inyectar muchas de las funciones primitivas (definidas en [`builtins.c`](https://github.com/JuliaLang/julia/blob/master/src/builtins.c)) para varias combinaciones de tipos de argumentos.

Otras partes de codegen son manejadas por varios archivos auxiliares:

  * [`debuginfo.cpp`](https://github.com/JuliaLang/julia/blob/master/src/debuginfo.cpp)

    Maneja las trazas de retroceso para funciones JIT
  * [`ccall.cpp`](https://github.com/JuliaLang/julia/blob/master/src/ccall.cpp)

    Maneja el ccall y llvmcall FFI, junto con varios archivos `abi_*.cpp`
  * [`intrinsics.cpp`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp)

    Maneja la emisión de varias funciones intrínsecas de bajo nivel.

!!! sidebar "Bootstrapping"
    El proceso de crear una nueva imagen del sistema se llama "bootstrapping".

    La etimología de esta palabra proviene de la frase "levantarse por las propias botas", y se refiere a la idea de comenzar desde un conjunto muy limitado de funciones y definiciones disponibles y terminar con la creación de un entorno completo.


## [System Image](@id dev-sysimg)

La imagen del sistema es un archivo comprimido precompilado de un conjunto de archivos de Julia. El archivo `sys.ji` distribuido con Julia es una de estas imágenes del sistema, generada al ejecutar el archivo [`sysimg.jl`](https://github.com/JuliaLang/julia/blob/master/base/sysimg.jl), y serializando el entorno resultante (incluyendo Tipos, Funciones, Módulos y todos los demás valores definidos) en un archivo. Por lo tanto, contiene una versión congelada de los módulos `Main`, `Core` y `Base` (y cualquier otra cosa que estuviera en el entorno al final del arranque). Este serializador/deserializador está implementado por [`jl_save_system_image`/`jl_restore_system_image` in `staticdata.c`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c).

Si no hay un archivo sysimg (`jl_options.image_file == NULL`), esto también implica que se dio `--build` en la línea de comandos, por lo que el resultado final debería ser un nuevo archivo sysimg. Durante la inicialización de Julia, se crean los módulos mínimos `Core` y `Main`. Luego, se evalúa un archivo llamado `boot.jl` desde el directorio actual. Julia luego evalúa cualquier archivo dado como un argumento de línea de comandos hasta que llega al final. Finalmente, guarda el entorno resultante en un archivo "sysimg" para usarlo como punto de partida para una futura ejecución de Julia.
