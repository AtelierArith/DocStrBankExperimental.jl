# System Image Building

## [Building the Julia system image](@id Building-the-Julia-system-image)

Julia se envía con una imagen de sistema preanalizada que contiene el contenido del módulo `Base`, llamada `sys.ji`. Este archivo también se compila previamente en una biblioteca compartida llamada `sys.{so,dll,dylib}` en tantas plataformas como sea posible, para ofrecer tiempos de inicio considerablemente mejorados. En sistemas que no se envían con un archivo de imagen de sistema precompilado, se puede generar a partir de los archivos fuente enviados en la carpeta `DATAROOTDIR/julia/base` de Julia.

Julia generará por defecto su imagen del sistema en la mitad de los hilos del sistema disponibles. Esto puede ser controlado por la variable de entorno [`JULIA_IMAGE_THREADS`](@ref JULIA_IMAGE_THREADS).

Esta operación es útil por múltiples razones. Un usuario puede:

  * Construya una imagen de sistema de biblioteca compartida precompilada en una plataforma que no se envió con una, mejorando así los tiempos de inicio.
  * Modifica `Base`, reconstruye la imagen del sistema y utiliza el nuevo `Base` la próxima vez que se inicie Julia.
  * Incluye un archivo `userimg.jl` que incluya paquetes en la imagen del sistema, creando así una imagen del sistema que tenga paquetes incrustados en el entorno de inicio.

El [`PackageCompiler.jl` package](https://github.com/JuliaLang/PackageCompiler.jl) contiene funciones de envoltura convenientes para automatizar este proceso.

## [System image optimized for multiple microarchitectures](@id sysimg-multi-versioning)

La imagen del sistema se puede compilar simultáneamente para múltiples microarquitecturas de CPU bajo el mismo conjunto de instrucciones (ISA). Se pueden crear múltiples versiones de la misma función con un punto de despacho mínimo insertado en funciones compartidas para aprovechar diferentes extensiones de ISA u otras características de microarquitectura. La versión que ofrezca el mejor rendimiento se seleccionará automáticamente en tiempo de ejecución en función de las características de CPU disponibles.

### Specifying multiple system image targets

Una imagen de sistema de múltiples microarquitecturas se puede habilitar pasando múltiples objetivos durante la compilación de la imagen del sistema. Esto se puede hacer ya sea con la opción de make [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) o con la opción de línea de comandos `-C` al ejecutar manualmente el comando de compilación. Los múltiples objetivos se separan por `;` en la cadena de opciones. La sintaxis para cada objetivo es un nombre de CPU seguido de múltiples características separadas por `,`. Todas las características soportadas por LLVM son compatibles y una característica se puede deshabilitar con un prefijo `-`. (El prefijo `+` también se permite y se ignora para ser consistente con la sintaxis de LLVM). Además, se admiten algunas características especiales para controlar el comportamiento de clonación de funciones.

!!! note
    Es una buena práctica especificar ya sea `clone_all` o `base(<n>)` para cada objetivo aparte del primero. Esto hace explícito qué objetivos tienen todas las funciones clonadas y cuáles objetivos se basan en otros objetivos. Si no se hace esto, el comportamiento predeterminado es no clonar cada función y usar la definición de función del primer objetivo como la opción de respaldo cuando no se clona una función.


1. `clonar_todo`

    Por defecto, solo se clonarán las funciones que tengan más probabilidades de beneficiarse de las características de la microarquitectura. Sin embargo, cuando se especifica `clone_all` para un objetivo, **todas** las funciones en la imagen del sistema se clonarán para el objetivo. La forma negativa `-clone_all` se puede usar para evitar que la heurística incorporada clone todas las funciones.
2. `base(<n>)`

    Donde `<n>` es un marcador de posición para un número no negativo (por ejemplo, `base(0)`, `base(1)`). Por defecto, un objetivo parcialmente clonado (es decir, no `clone_all`) utilizará funciones del objetivo predeterminado (el primero especificado) si una función no está clonada. Este comportamiento se puede cambiar especificando una base diferente con la opción `base(<n>)`. El objetivo `n` (basado en 0) se utilizará como el objetivo base en lugar del predeterminado (el `0`-ésimo). El objetivo base debe ser `0` o otro objetivo `clone_all`. Especificar un objetivo que no sea `clone_all` como el objetivo base causará un error.
3. `opt_size`

    Esto hace que la función para el objetivo se optimice para el tamaño cuando no hay un impacto significativo en el rendimiento en tiempo de ejecución. Esto corresponde a la opción `-Os` de GCC y Clang.
4. `min_size`

    Esto hace que la función para el objetivo se optimice para el tamaño, lo que podría tener un impacto significativo en el rendimiento en tiempo de ejecución. Esto corresponde a la opción `-Oz` de Clang.

Como ejemplo, en el momento de escribir esto, la siguiente cadena se utiliza en la creación de los binarios oficiales `x86_64` de Julia que se pueden descargar de julialang.org:

```
generic;sandybridge,-xsaveopt,clone_all;haswell,-rdrnd,base(1)
```

Esto crea una imagen del sistema con tres objetivos separados; uno para un procesador genérico `x86_64`, uno con una ISA `sandybridge` (excluyendo explícitamente `xsaveopt`) que clona explícitamente todas las funciones, y uno dirigido a la ISA `haswell`, basado en la versión sysimg de `sandybridge`, y también excluyendo `rdrnd`. Cuando una implementación de Julia carga el sysimg generado, verificará el procesador host en busca de banderas de capacidad de CPU coincidentes, habilitando el nivel de ISA más alto posible. Tenga en cuenta que el nivel base (`genérico`) requiere la instrucción `cx16`, que está deshabilitada en algunos software de virtualización y debe habilitarse para que se cargue el objetivo `genérico`. Alternativamente, se podría generar un sysimg con el objetivo `genérico,-cx16` para una mayor compatibilidad, sin embargo, tenga en cuenta que esto puede causar problemas de rendimiento y estabilidad en algún código.

### Implementation overview

Este es un breve resumen de las diferentes partes involucradas en la implementación. Consulta los comentarios del código para obtener más detalles sobre cada componente.

1. Compilación de imagen del sistema

    La decisión de análisis y clonación se realiza en `src/processor*`. Actualmente, soportamos la clonación de funciones basadas en la presencia de bucles, instrucciones simd u otras operaciones matemáticas (por ejemplo, fastmath, fma, muladd). Esta información se pasa a `src/llvm-multiversioning.cpp`, que realiza la clonación real. Además de realizar la clonación e insertar espacios de despacho (ver comentarios en `MultiVersioning::runOnModule` sobre cómo se hace esto), el pase también genera metadatos para que el tiempo de ejecución pueda cargar e inicializar la imagen del sistema correctamente. Una descripción detallada de los metadatos está disponible en `src/processor.h`.
2. Cargando imagen del sistema

    La carga y la inicialización de la imagen del sistema se realizan en `src/processor*` mediante el análisis de los metadatos guardados durante la generación de la imagen del sistema. La detección de características del host y la decisión de selección se realizan en `src/processor_*.cpp` dependiendo de la ISA. La selección del objetivo preferirá una coincidencia exacta del nombre de la CPU, un tamaño de registro vectorial más grande y un mayor número de características. Una visión general de este proceso se encuentra en `src/processor.cpp`.
