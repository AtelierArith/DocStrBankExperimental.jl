# Working with LLVM

Esto no es un reemplazo de la documentación de LLVM, sino una colección de consejos para trabajar en LLVM para Julia.

## Overview of Julia to LLVM Interface

Julia enlaza dinámicamente con LLVM por defecto. Compila con `USE_LLVM_SHLIB=0` para enlazar de forma estática.

El código para bajar el AST de Julia a LLVM IR o interpretarlo directamente está en el directorio `src/`.

| File                             | Description                                                        |
|:-------------------------------- |:------------------------------------------------------------------ |
| `aotcompile.cpp`                 | Compiler C-interface entry and object file emission                |
| `builtins.c`                     | Builtin functions                                                  |
| `ccall.cpp`                      | Lowering [`ccall`](@ref)                                           |
| `cgutils.cpp`                    | Lowering utilities, notably for array and tuple accesses           |
| `codegen.cpp`                    | Top-level of code generation, pass list, lowering builtins         |
| `debuginfo.cpp`                  | Tracks debug information for JIT code                              |
| `disasm.cpp`                     | Handles native object file and JIT code diassembly                 |
| `gf.c`                           | Generic functions                                                  |
| `intrinsics.cpp`                 | Lowering intrinsics                                                |
| `jitlayers.cpp`                  | JIT-specific code, ORC compilation layers/utilities                |
| `llvm-alloc-helpers.cpp`         | Julia-specific escape analysis                                     |
| `llvm-alloc-opt.cpp`             | Custom LLVM pass to demote heap allocations to the stack           |
| `llvm-cpufeatures.cpp`           | Custom LLVM pass to lower CPU-based functions (e.g. haveFMA)       |
| `llvm-demote-float16.cpp`        | Custom LLVM pass to lower 16b float ops to 32b float ops           |
| `llvm-final-gc-lowering.cpp`     | Custom LLVM pass to lower GC calls to their final form             |
| `llvm-gc-invariant-verifier.cpp` | Custom LLVM pass to verify Julia GC invariants                     |
| `llvm-julia-licm.cpp`            | Custom LLVM pass to hoist/sink Julia-specific intrinsics           |
| `llvm-late-gc-lowering.cpp`      | Custom LLVM pass to root GC-tracked values                         |
| `llvm-lower-handlers.cpp`        | Custom LLVM pass to lower try-catch blocks                         |
| `llvm-muladd.cpp`                | Custom LLVM pass for fast-match FMA                                |
| `llvm-multiversioning.cpp`       | Custom LLVM pass to generate sysimg code on multiple architectures |
| `llvm-propagate-addrspaces.cpp`  | Custom LLVM pass to canonicalize addrspaces                        |
| `llvm-ptls.cpp`                  | Custom LLVM pass to lower TLS operations                           |
| `llvm-remove-addrspaces.cpp`     | Custom LLVM pass to remove Julia addrspaces                        |
| `llvm-remove-ni.cpp`             | Custom LLVM pass to remove Julia non-integral addrspaces           |
| `llvm-simdloop.cpp`              | Custom LLVM pass for [`@simd`](@ref)                               |
| `pipeline.cpp`                   | New pass manager pipeline, pass pipeline parsing                   |
| `sys.c`                          | I/O and operating system utility functions                         |

Algunos de los archivos `.cpp` forman un grupo que se compila en un solo objeto.

La diferencia entre un intrínseco y un incorporado es que un incorporado es una función de primera clase que se puede usar como cualquier otra función de Julia. Un intrínseco solo puede operar en datos no empaquetados, y por lo tanto, sus argumentos deben estar tipados estáticamente.

### [Alias Analysis](@id LLVM-Alias-Analysis)

Julia actualmente utiliza LLVM's [Type Based Alias Analysis](https://llvm.org/docs/LangRef.html#tbaa-metadata). Para encontrar los comentarios que documentan las relaciones de inclusión, busca `static MDNode*` en `src/codegen.cpp`.

La opción `-O` habilita [Basic Alias Analysis](https://llvm.org/docs/AliasAnalysis.html#the-basic-aa-pass) de LLVM.

## Building Julia with a different version of LLVM

La versión predeterminada de LLVM se especifica en `deps/llvm.version`. Puedes anularla creando un archivo llamado `Make.user` en el directorio de nivel superior y agregando una línea como:

```
LLVM_VER = 13.0.0
```

Además de los números de versión de LLVM, también puedes usar `DEPS_GIT = llvm` en combinación con `USE_BINARYBUILDER_LLVM = 0` para compilar contra la última versión de desarrollo de LLVM.

También puedes especificar construir una versión de depuración de LLVM, configurando `LLVM_DEBUG = 1` o `LLVM_DEBUG = Release` en tu archivo `Make.user`. La primera será una construcción de LLVM completamente no optimizada y la última producirá una construcción optimizada de LLVM. Dependiendo de tus necesidades, la última será suficiente y es bastante más rápida. Si usas `LLVM_DEBUG = Release`, también querrás establecer `LLVM_ASSERTIONS = 1` para habilitar diagnósticos para diferentes pases. Solo `LLVM_DEBUG = 1` implica esa opción por defecto.

## Passing options to LLVM

Puedes pasar opciones a LLVM a través de la variable de entorno [`JULIA_LLVM_ARGS`](@ref JULIA_LLVM_ARGS). Aquí hay configuraciones de ejemplo usando la sintaxis de `bash`:

  * `export JULIA_LLVM_ARGS=-print-after-all` volcará IR después de cada pase.
  * `export JULIA_LLVM_ARGS=-debug-only=loop-vectorize` volcará diagnósticos `DEBUG(...)` de LLVM para el vectorizador de bucles. Si recibes advertencias sobre "Argumento de línea de comando desconocido", reconstruye LLVM con `LLVM_ASSERTIONS = 1`.
  * `export JULIA_LLVM_ARGS=-help` muestra una lista de opciones disponibles. `export JULIA_LLVM_ARGS=-help-hidden` muestra aún más.
  * `export JULIA_LLVM_ARGS="-fatal-warnings -print-options"` es un ejemplo de cómo usar múltiples opciones.

### Useful `JULIA_LLVM_ARGS` parameters

  * `-print-after=PASS`: imprime el IR después de cualquier ejecución de `PASS`, útil para verificar los cambios realizados por un pase.
  * `-print-before=PASS`: imprime el IR antes de cualquier ejecución de `PASS`, útil para verificar la entrada a un pase.
  * `-print-changed`: imprime el IR cada vez que un pase cambia el IR, útil para reducir qué pases están causando problemas.
  * `-print-(before|after)=MARKER-PASS`: el pipeline de Julia incluye una serie de pases de marcador en el pipeline, que se pueden utilizar para identificar dónde ocurren problemas u optimizaciones. Un pase de marcador se define como un pase que aparece una vez en el pipeline y no realiza transformaciones en el IR, y solo es útil para apuntar a print-before/print-after. Actualmente, los siguientes pases de marcador existen en el pipeline:

      * Antes de la optimización
      * AntesDeLaSimplificaciónTemprana
      * DespuésDeLaSimplificaciónTemprana
      * AntesDeLaOptimizaciónTemprana
      * DespuésDeLaOptimizaciónTemprana
      * AntesDelBucleOptimización
      * AntesLICM
      * DespuésLICM
      * AntesDeLaSimplificaciónDelBucle
      * DespuésDeLaSimplificaciónDelBucle
      * DespuésDeOptimizaciónDeBucle
      * AntesDeOptimizaciónEscalar
      * DespuésDeOptimizaciónEscalar
      * AntesDeLaVectorización
      * DespuésDeVectorización
      * AntesDelBajoNivelIntrínseco
      * DespuésDelBajoIntrínseco
      * Antes de la limpieza
      * Después de la limpieza
      * DespuésDeOptimización
  * `-time-passes`: imprime el tiempo gastado en cada pase, útil para identificar qué pases están tardando mucho tiempo.
  * `-print-module-scope`: se utiliza junto con `-print-(before|after)`, obtiene todo el módulo en lugar de la unidad IR recibida por el pase.
  * `-debug`: imprime mucha información de depuración a lo largo de LLVM
  * `-debug-only=NAME`, imprime declaraciones de depuración de archivos con `DEBUG_TYPE` definido como `NAME`, útil para obtener contexto adicional sobre un problema.

## Debugging LLVM transformations in isolation

En ocasiones, puede ser útil depurar las transformaciones de LLVM de forma aislada del resto del sistema Julia, por ejemplo, porque reproducir el problema dentro de `julia` tomaría demasiado tiempo, o porque se quiere aprovechar las herramientas de LLVM (por ejemplo, bugpoint).

Para comenzar, puedes instalar las herramientas de desarrollo para trabajar con LLVM a través de:

```
make -C deps install-llvm-tools
```

Para obtener IR no optimizado para toda la imagen del sistema, pase la opción `--output-unopt-bc unopt.bc` al proceso de construcción de la imagen del sistema, que generará el IR no optimizado en un archivo `unopt.bc`. Este archivo se puede pasar a las herramientas de LLVM como de costumbre. `libjulia` puede funcionar como un complemento de paso de LLVM y se puede cargar en las herramientas de LLVM, para hacer que los pasos específicos de Julia estén disponibles en este entorno. Además, expone el meta-paso `-julia`, que ejecuta toda la tubería de pasos de Julia sobre el IR. Como ejemplo, para generar una imagen del sistema con el antiguo administrador de pasos, se podría hacer:

```

llc -o sys.o opt.bc
cc -shared -o sys.so sys.o
```

Para generar una imagen del sistema con el nuevo administrador de contraseñas, se podría hacer:

```
opt -load-pass-plugin=libjulia-codegen.so --passes='julia' -o opt.bc unopt.bc
llc -o sys.o opt.bc
cc -shared -o sys.so sys.o
```

Esta imagen del sistema puede ser cargada por `julia` como de costumbre.

También es posible volcar un módulo LLVM IR para solo una función de Julia, usando:

```julia
fun, T = +, Tuple{Int,Int} # Substitute your function of interest here
optimize = false
open("plus.ll", "w") do file
    println(file, InteractiveUtils._dump_function(fun, T, false, false, false, true, :att, optimize, :default, false))
end
```

Estos archivos se pueden procesar de la misma manera que el IR sysimg no optimizado mostrado arriba.

## Running the LLVM test suite

Para ejecutar las pruebas de llvm localmente, primero necesitas instalar las herramientas, construir julia, luego puedes ejecutar las pruebas:

```
make -C deps install-llvm-tools
make -j julia-src-release
make -C test/llvmpasses
```

Si deseas ejecutar los archivos de prueba individuales directamente, a través de los comandos en la parte superior de cada archivo de prueba, el primer paso aquí habrá instalado las herramientas en `./usr/tools/opt`. Luego querrás reemplazar manualmente `%s` con el nombre del archivo de prueba.

## Improving LLVM optimizations for Julia

Mejorar la generación de código de LLVM generalmente implica cambiar la reducción de Julia para que sea más amigable con los pases de LLVM, o mejorar un pase.

Si estás planeando mejorar un pase, asegúrate de leer el [LLVM developer policy](https://llvm.org/docs/DeveloperPolicy.html). La mejor estrategia es crear un ejemplo de código en una forma donde puedas usar la herramienta `opt` de LLVM para estudiarlo y el pase de interés en aislamiento.

1. Create an example Julia code of interest.
2. Usa `JULIA_LLVM_ARGS=-print-after-all` para volcar el IR.
3. Selecciona el IR en el punto justo antes de que se ejecute el pase de interés.
4. Elimina los metadatos de depuración y corrige manualmente los metadatos TBAA.

El último paso es intensivo en mano de obra. Se agradecerían sugerencias sobre una mejor manera.

## The jlcall calling convention

Julia tiene una convención de llamada genérica para código no optimizado, que se ve algo así:

```c
jl_value_t *any_unoptimized_call(jl_value_t *, jl_value_t **, int);
```

donde el primer argumento es el objeto de función en caja, el segundo argumento es un array de argumentos en la pila y el tercero es el número de argumentos. Ahora, podríamos realizar una reducción directa y emitir un alloca para el array de argumentos. Sin embargo, esto traicionaría la naturaleza SSA de los usos en el sitio de llamada, haciendo que las optimizaciones (incluida la colocación de raíces de GC) sean significativamente más difíciles. En su lugar, lo emitimos de la siguiente manera:

```llvm
call %jl_value_t *@julia.call(jl_value_t *(*)(...) @any_unoptimized_call, %jl_value_t *%arg1, %jl_value_t *%arg2)
```

Esto nos permite retener la naturaleza SSA de los usos a lo largo del optimizador. La colocación de la raíz GC más tarde reducirá esta llamada a la ABI C original.

## GC root placement

La colocación de raíces de GC se realiza mediante un pase de LLVM tarde en la tubería de pases. Hacer la colocación de raíces de GC tan tarde permite a LLVM realizar optimizaciones más agresivas en torno al código que requiere raíces de GC, así como también nos permite reducir el número de raíces de GC requeridas y las operaciones de almacenamiento de raíces de GC (dado que LLVM no entiende nuestro GC, de otro modo no sabría qué se le permite y qué no se le permite hacer con los valores almacenados en el marco de GC, por lo que lo hará de manera conservadora y hará muy poco). Como ejemplo, considera un camino de error.

```julia
if some_condition()
    #= Use some variables maybe =#
    error("An error occurred")
end
```

Durante la reducción de raíces de GC, LLVM puede descubrir que la condición siempre es falsa y puede eliminar el bloque básico. Sin embargo, si la reducción de raíces de GC se realiza temprano, las ranuras de raíces de GC utilizadas en el bloque eliminado, así como cualquier valor mantenido vivo en esas ranuras solo porque se usaron en la ruta de error, serían mantenidos vivos por LLVM. Al realizar la reducción de raíces de GC tarde, le damos a LLVM la licencia para realizar cualquiera de sus optimizaciones habituales (reducción constante, eliminación de código muerto, etc.), sin tener que preocuparse (demasiado) por qué valores pueden o no estar rastreados por GC.

Sin embargo, para poder realizar la colocación tardía de raíces de GC, necesitamos poder identificar a) qué punteros son rastreados por GC y b) todos los usos de dichos punteros. El objetivo del pase de colocación de GC es, por lo tanto, simple:

Minimizar el número de raíces GC necesarias/almacenamientos a ellas, sujeto a la restricción de que en cada punto seguro, cualquier puntero rastreado por GC vivo (es decir, para el cual hay un camino después de este punto que contiene un uso de este puntero) esté en algún espacio de GC.

### Representation

La dificultad principal es, por lo tanto, elegir una representación IR que nos permita identificar punteros rastreados por GC y sus usos, incluso después de que el programa haya sido procesado por el optimizador. Nuestro diseño hace uso de tres características de LLVM para lograr esto:

  * Espacios de direcciones personalizados
  * Paquetes de Operandos
  * Punteros no integrales

Los espacios de direcciones personalizados nos permiten etiquetar cada punto con un entero que debe ser preservado a través de optimizaciones. El compilador no puede insertar conversiones entre espacios de direcciones que no existían en el programa original y nunca debe cambiar el espacio de direcciones de un puntero en una operación de carga/almacenamiento/etc. Esto nos permite anotar qué punteros son rastreados por el GC de una manera resistente a optimizaciones. Tenga en cuenta que los metadatos no podrían lograr el mismo propósito. Se supone que los metadatos siempre deben ser descartables sin alterar la semántica del programa. Sin embargo, no identificar un puntero rastreado por el GC altera drásticamente el comportamiento del programa resultante: probablemente se bloqueará o devolverá resultados incorrectos. Actualmente usamos tres espacios de direcciones diferentes (sus números están definidos en `src/codegen_shared.cpp`):

  * GC Punteros Rastreables (actualmente 10): Estos son punteros a valores empaquetados que pueden ser colocados en un marco de GC. Es equivalente de manera aproximada a un puntero `jl_value_t*` en el lado de C. N.B. Es ilegal tener un puntero en este espacio de direcciones que no pueda ser almacenado en un slot de GC.
  * Punteros derivados (actualmente 11): Estos son punteros que se derivan de algún puntero rastreado por el GC. Los usos de estos punteros generan usos del puntero original. Sin embargo, no es necesario que ellos mismos sean conocidos por el GC. La pasada de colocación de raíces del GC DEBE siempre encontrar el puntero rastreado por el GC del cual se deriva este puntero y usarlo como el puntero a la raíz.
  * Punteros Raíz de Llamada (actualmente 12): Este es un espacio de direcciones utilitario para expresar la noción de un valor raíz de llamada. Todos los valores de este espacio de direcciones DEBEN ser almacenables en una raíz de GC (aunque es posible relajar esta condición en el futuro), pero a diferencia de los otros punteros, no necesitan estar enraizados si se pasan a una llamada (aún deben estar enraizados si están activos a través de otro punto seguro entre la definición y la llamada).
  * Punteros cargados desde el objeto rastreado (actualmente 13): Esto es utilizado por arreglos, que a su vez contienen un puntero a los datos administrados. Esta área de datos es propiedad del arreglo, pero no es un objeto rastreado por el GC por sí mismo. El compilador garantiza que mientras este puntero esté activo, el objeto del cual se cargó este puntero seguirá estando activo.

### Invariants

La pasada de colocación de GC root utiliza varios invariantes, que deben ser observados por el frontend y son preservados por el optimizador.

Primero, solo se permiten las siguientes conversiones de espacio de direcciones:

  * 0->{Rastreado,Derivado,RaízDeLlamada}: Se permite degradar un puntero no rastreado a cualquiera de los otros. Sin embargo, tenga en cuenta que el optimizador tiene un amplio margen para no enraizar tal valor. Nunca es seguro tener un valor en el espacio de direcciones 0 en ninguna parte del programa si es (o se deriva de) un valor que requiere una raíz de GC.
  * Rastreado->Derivado: Esta es la ruta de descomposición estándar para los valores interiores. El pase de colocación buscará estos para identificar el puntero base para cualquier uso.
  * Rastreado->CalleeRooted: El espacio de direcciones CalleeRooted sirve meramente como una pista de que no se requiere una raíz de GC. Sin embargo, tenga en cuenta que la decadencia Derived->CalleeRooted está prohibida, ya que los punteros generalmente deberían ser almacenables en un slot de GC, incluso en este espacio de direcciones.

Ahora consideremos qué constituye un uso:

  * Cargas cuyos valores cargados están en uno de los espacios de direcciones
  * Almacena un valor en uno de los espacios de direcciones a una ubicación
  * Almacena en un puntero en uno de los espacios de direcciones
  * Llamadas para las cuales un valor en uno de los espacios de direcciones es un operando
  * Llamadas en ABI jlcall, para las cuales el array de argumentos contiene un valor
  * Por favor, proporciona el contenido en Markdown que deseas traducir al español.

Permitimos explícitamente cargas/almacenamientos y llamadas simples en los espacios de direcciones Tracked/Derived. Los elementos de los arreglos de argumentos de jlcall deben estar siempre en el espacio de direcciones Tracked (se requiere por el ABI que sean punteros válidos `jl_value_t*`). Lo mismo es cierto para las instrucciones de retorno (aunque cabe señalar que se permite que los argumentos de retorno de estructuras tengan cualquiera de los espacios de direcciones). El único uso permitido de un puntero de espacio de direcciones CalleeRooted es pasarlo a una llamada (que debe tener un operando de tipo apropiado).

Además, no permitimos `getelementptr` en el espacio de direcciones Tracked. Esto se debe a que, a menos que la operación sea un noop, el puntero resultante no será almacenable válidamente en un slot de GC y, por lo tanto, puede no estar en este espacio de direcciones. Si se requiere tal puntero, debe ser reducido a addrspace Derived primero.

Por último, no permitimos instrucciones `inttoptr`/`ptrtoint` en estos espacios de direcciones. Tener estas instrucciones significaría que algunos valores `i64` están realmente rastreados por el GC. Esto es problemático, porque rompe el requisito establecido de que podemos identificar punteros relevantes para el GC. Esta invariante se logra utilizando la función de "punteros no integrales" de LLVM, que es nueva en LLVM 5.0. Prohíbe al optimizador realizar optimizaciones que introducirían estas operaciones. Tenga en cuenta que aún podemos insertar constantes estáticas en tiempo de JIT utilizando `inttoptr` en el espacio de direcciones 0 y luego decaer al espacio de direcciones apropiado después.

### Supporting [`ccall`](@ref)

Un aspecto importante que falta en la discusión hasta ahora es el manejo de [`ccall`](@ref). `4d61726b646f776e2e436f64652822222c20226363616c6c2229_40726566` tiene la característica peculiar de que la ubicación y el alcance de un uso no coinciden. Como ejemplo, considere:

```julia
A = randn(1024)
ccall(:foo, Cvoid, (Ptr{Float64},), A)
```

Al bajar, el compilador insertará una conversión del arreglo al puntero que elimina la referencia al valor del arreglo. Sin embargo, por supuesto, debemos asegurarnos de que el arreglo permanezca vivo mientras estamos haciendo el [`ccall`](@ref). Para entender cómo se hace esto, veamos un posible descenso hipotético aproximado del código anterior:

```julia
return $(Expr(:foreigncall, :(:foo), Cvoid, svec(Ptr{Float64}), 0, :(:ccall), Expr(:foreigncall, :(:jl_array_ptr), Ptr{Float64}, svec(Any), 0, :(:ccall), :(A)), :(A)))
```

El último `:(A)`, es una lista de argumentos extra insertada durante la reducción que informa al generador de código qué valores de nivel Julia necesitan mantenerse vivos durante la duración de este [`ccall`](@ref). Luego tomamos esta información y la representamos en un "paquete de operandos" a nivel de IR. Un paquete de operandos es esencialmente un uso falso que se adjunta al sitio de llamada. A nivel de IR, esto se ve así:

```llvm
call void inttoptr (i64 ... to void (double*)*)(double* %5) [ "jl_roots"(%jl_value_t addrspace(10)* %A) ]
```

El paso de colocación de raíces de GC tratará el paquete de operandos `jl_roots` como si fuera un operando regular. Sin embargo, como paso final, después de que se inserten las raíces de GC, eliminará el paquete de operandos para evitar confundir la selección de instrucciones.

### Supporting [`pointer_from_objref`](@ref)

[`pointer_from_objref`](@ref) es especial porque requiere que el usuario tome el control explícito de la raíz del GC. Según nuestras invariantes anteriores, esta función es ilegal, porque realiza un cast de espacio de direcciones de 10 a 0. Sin embargo, puede ser útil en ciertas situaciones, por lo que proporcionamos un intrínseco especial:

```llvm
declared %jl_value_t *julia.pointer_from_objref(%jl_value_t addrspace(10)*)
```

que se reduce al espacio de direcciones correspondiente después de la reducción de la raíz GC. Sin embargo, tenga en cuenta que al usar este intrínseco, el llamador asume toda la responsabilidad de asegurarse de que el valor en cuestión esté enraizado. Además, este intrínseco no se considera un uso, por lo que la pasada de colocación de raíz GC no proporcionará una raíz GC para la función. Como resultado, el enraizamiento externo debe organizarse mientras el valor aún esté rastreado por el sistema. Es decir, no es válido intentar usar el resultado de esta operación para establecer una raíz global; el optimizador puede haber eliminado ya el valor.

### Keeping values alive in the absence of uses

En ciertos casos, es necesario mantener un objeto vivo, incluso si no hay un uso visible por el compilador de dicho objeto. Este puede ser el caso para código de bajo nivel que opera directamente en la representación en memoria de un objeto o código que necesita interactuar con código C. Para permitir esto, proporcionamos las siguientes intrínsecas a nivel de LLVM:

```
token @llvm.julia.gc_preserve_begin(...)
void @llvm.julia.gc_preserve_end(token)
```

(El `llvm.` en el nombre es necesario para poder usar el tipo `token`). La semántica de estas intrínsecas es la siguiente: En cualquier punto seguro que está dominado por una llamada a `gc_preserve_begin`, pero que no está dominado por una llamada correspondiente a `gc_preserve_end` (es decir, una llamada cuyo argumento es el token devuelto por una llamada a `gc_preserve_begin`), los valores pasados como argumentos a esa `gc_preserve_begin` se mantendrán vivos. Tenga en cuenta que la `gc_preserve_begin` aún cuenta como un uso regular de esos valores, por lo que la semántica estándar de duración asegurará que los valores se mantendrán vivos antes de entrar en la región de preservación.
