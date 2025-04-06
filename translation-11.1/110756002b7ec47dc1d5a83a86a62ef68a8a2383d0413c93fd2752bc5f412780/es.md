# Custom LLVM Passes

Julia tiene una serie de pases personalizados de LLVM. En términos generales, se pueden clasificar en pases que deben ejecutarse para mantener la semántica de Julia y pases que aprovechan la semántica de Julia para optimizar el IR de LLVM.

## Semantic Passes

Estos pases se utilizan para transformar LLVM IR en código que es legal para ser ejecutado en una CPU. Su propósito principal es permitir que se emita un IR más simple por parte de codegen, lo que a su vez permite que otros pases de LLVM optimicen patrones comunes.

### CPUFeatures

  * Nombre de archivo: `llvm-cpufeatures.cpp`
  * Nombre de la clase: `CPUFeaturesPass`
  * Nombre de la opción: `module(CPUFeatures)`

Este pase reduce el intrínseco `julia.cpu.have_fma.(f32|f64)` a verdadero o falso, dependiendo de la arquitectura de destino y las características de destino presentes en la función. Este intrínseco se utiliza a menudo para determinar si el uso de algoritmos dependientes de operaciones rápidas [fused multiply-add](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add) es mejor que el uso de algoritmos estándar que no dependen de tales instrucciones.

### DemoteFloat16

  * Nombre de archivo: `llvm-demote-float16.cpp`
  * ClassName: `DemoteFloat16Pass`
  * Nombre de la opción `function(DemoteFloat16)`

Este pase reemplaza [float16](https://en.wikipedia.org/wiki/Half-precision_floating-point_format) operaciones con operaciones float32 en arquitecturas que no soportan nativamente operaciones float16. Esto se hace insertando instrucciones `fpext` y `fptrunc` alrededor de cualquier operación float16. En arquitecturas que sí soportan operaciones nativas float16, este pase es un no-op.

### LateGCLowering

  * Nombre de archivo: `llvm-late-gc-lowering.cpp`
  * Nombre de la clase: `LateLowerGCPass`
  * Nombre de la opción: `function(LateLowerGCFrame)`

Este pase realiza la mayor parte del trabajo de enraizamiento de GC necesario para rastrear punteros entre los puntos seguros de GC. También reduce varios intrínsecos a su traducción de instrucción correspondiente, y se le permite violar las invariantes no integrales establecidas anteriormente (`pointer_from_objref` se reduce a una instrucción `ptrtoint` aquí). Este pase ocupa típicamente la mayor parte del tiempo de todos los pases personalizados de Julia, debido a su algoritmo de flujo de datos para minimizar el número de objetos vivos en cualquier punto seguro.

### FinalGCLowering

  * Nombre de archivo: `llvm-final-gc-lowering.cpp`
  * Nombre de la clase: `FinalLowerGCPass`
  * Nombre de la opción: `module(FinalLowerGC)`

Este pase reduce algunos últimos intrínsecos a su forma final, dirigiéndose a funciones en la biblioteca `libjulia`. Separar esto de `LateGCLowering` permite que otros backends (compilación en GPU) proporcionen sus propias reducciones personalizadas para estos intrínsecos, lo que permite que el pipeline de Julia se utilice en esos backends también.

### LowerHandlers

  * Nombre de archivo: `llvm-lower-handlers.cpp`
  * Nombre de la clase: `LowerExcHandlersPass`
  * Nombre de la opción: `function(LowerExcHandlers)`

Este pase reduce los intrínsecos de manejo de excepciones a llamadas a funciones de tiempo de ejecución que se llaman realmente al manejar excepciones.

### RemoveNI

  * Nombre de archivo: `llvm-remove-ni.cpp`
  * Nombre de la clase: `RemoveNIPass`
  * Nombre de la opción: `module(RemoveNI)`

Este pase elimina los espacios de direcciones no integrales de la cadena de datalayout del módulo. Esto permite que el backend reduzca los espacios de direcciones personalizados de Julia directamente a código de máquina, sin una costosa reescritura de cada operación de puntero al espacio de direcciones 0.

### SIMDLoop

  * Nombre de archivo: `llvm-simdloop.cpp`
  * Nombre de la clase: `LowerSIMDLoopPass`
  * Nombre de la opción: `loop(LowerSIMDLoop)`

Este pase actúa como el controlador principal de la anotación `@simd`. Codegen inserta un marcador `!llvm.loopid` en la rama de retroceso de un bucle, que este pase utiliza para identificar bucles que fueron marcados originalmente con `@simd`. Luego, este pase busca una cadena de operaciones de punto flotante que forman una reducción y agrega las banderas de matemáticas rápidas `contract` y `reassoc` para permitir la reasociación (y, por lo tanto, la vectorización). Este pase no preserva ni la información del bucle ni la corrección de la inferencia, por lo que puede violar la semántica de Julia de maneras sorprendentes. Si el bucle también fue anotado con `ivdep`, entonces el pase marca el bucle como si no tuviera dependencias transportadas por el bucle (el comportamiento resultante es indefinido si la anotación del usuario fue incorrecta o se aplica al bucle equivocado).

### LowerPTLS

  * Nombre de archivo: `llvm-ptls.cpp`
  * Nombre de la clase: `LowerPTLSPass`
  * Nombre de la opción: `module(LowerPTLSPass)`

Este pase reduce los intrínsecos locales de hilo de Julia a instrucciones de ensamblador. Julia depende del almacenamiento local de hilo para la recolección de basura y la programación de tareas en múltiples hilos. Al compilar código para imágenes del sistema e imágenes de paquetes, este pase reemplaza las llamadas a intrínsecos con cargas de variables globales que se inicializan en el momento de la carga.

Si codegen produce una función con un argumento y convención de llamada `swiftself`, este pase asume que el argumento `swiftself` es el pgcstack y reemplazará los intrínsecos con ese argumento. Hacer esto proporciona mejoras de velocidad en arquitecturas que tienen accesos lentos a almacenamiento local de hilos.

### RemoveAddrspaces

  * Nombre de archivo: `llvm-remove-addrspaces.cpp`
  * Nombre de la clase: `RemoveAddrspacesPass`
  * Nombre de la opción: `module(RemoveAddrspaces)`

Este pase renombra punteros de un espacio de direcciones a otro espacio de direcciones. Esto se utiliza para eliminar espacios de direcciones específicos de Julia del IR de LLVM.

### RemoveJuliaAddrspaces

  * Nombre de archivo: `llvm-remove-addrspaces.cpp`
  * Nombre de la clase: `RemoveJuliaAddrspacesPass`
  * Nombre de la opción: `module(RemoveJuliaAddrspaces)`

Este pase elimina los espacios de direcciones específicos de Julia del IR de LLVM. Se utiliza principalmente para mostrar el IR de LLVM en un formato menos desordenado. Internamente, se implementa a partir del pase RemoveAddrspaces.

### Multiversioning

  * Nombre de archivo: `llvm-multiversioning.cpp`
  * Nombre de la clase: `MultiVersioningPass`
  * Nombre del módulo: `module(JuliaMultiVersioning)`

Este pase realiza modificaciones a un módulo para crear funciones que están optimizadas para ejecutarse en diferentes arquitecturas (ver sysimg.md y pkgimg.md para más detalles). En términos de implementación, clona funciones y aplica diferentes atributos específicos de destino a ellas para permitir que el optimizador utilice características avanzadas como la vectorización y la programación de instrucciones para esa plataforma. También crea cierta infraestructura para permitir que el cargador de imágenes de Julia seleccione la versión apropiada de la función a llamar según la arquitectura en la que se esté ejecutando el cargador. Los atributos específicos de destino son controlados por la bandera de módulo `julia.mv.specs`, que durante la compilación se deriva de la variable de entorno [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET). El pase también debe ser habilitado proporcionando una bandera de módulo `julia.mv.enable` con un valor de 1.

!!! warning
    El uso de `llvmcall` con multiversionado es peligroso. `llvmcall` permite el acceso a características que no suelen estar expuestas por las APIs de Julia, y por lo tanto, generalmente no están disponibles en todas las arquitecturas. Si el multiversionado está habilitado y se solicita la generación de código para una arquitectura de destino que no admite la característica requerida por una expresión `llvmcall`, es probable que LLVM genere un error, probablemente con un aborto y el mensaje `LLVM ERROR: Do not know how to split the result of this operator!`.


### GCInvariantVerifier

  * Nombre de archivo: `llvm-gc-invariant-verifier.cpp`
  * Nombre de la clase: `GCInvariantVerifierPass`
  * Nombre de la opción: `module(GCInvariantVerifier)`

Este pase se utiliza para verificar los invariantes de Julia sobre LLVM IR. Esto incluye cosas como la inexistencia de `ptrtoint` en [non-integral address spaces](https://llvm.org/docs/LangRef.html#non-integral-pointer-type) [^nislides] y la existencia solo de instrucciones `addrspacecast` bendecidas (Rastreado -> Derivado, 0 -> Rastreado, etc). No realiza transformaciones en IR.

[^nislides]: https://llvm.org/devmtg/2015-02/slides/chisnall-pointers-not-int.pdf

## Optimization Passes

Estos pases se utilizan para realizar transformaciones en LLVM IR que LLVM no realizará por sí mismo, por ejemplo, la propagación de la bandera de matemáticas rápidas, el análisis de escape y optimizaciones en funciones internas específicas de Julia. Utilizan el conocimiento sobre la semántica de Julia para llevar a cabo estas optimizaciones.

### CombineMulAdd

  * Nombre de archivo: `llvm-muladd.cpp`
  * Nombre de la clase: `CombineMulAddPass`
  * Nombre de la opción: `function(CombineMulAdd)`

Este pase sirve para optimizar la combinación particular de un `fmul` regular con un `fadd` rápido en un `fmul` de contrato con un `fadd` rápido. Esto es optimizado más tarde por el backend a una instrucción [fused multiply-add](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add), que puede proporcionar operaciones significativamente más rápidas a costa de más [unpredictable semantics](https://simonbyrne.github.io/notes/fastmath/).

!!! note
    Esta optimización solo ocurre cuando el `fmul` tiene un solo uso, que es el rápido `fadd`.


### AllocOpt

  * Nombre de archivo: `llvm-alloc-opt.cpp`
  * Nombre de la clase: `AllocOptPass`
  * Nombre de la opción: `function(AllocOpt)`

Julia no tiene el concepto de una pila de programas como un lugar para asignar objetos mutables. Sin embargo, asignar objetos en la pila reduce la presión del GC y es crítico para la compilación en GPU. Así, `AllocOpt` realiza la conversión de objetos de heap a pila que puede probar que no [escape](https://en.wikipedia.org/wiki/Escape_analysis) la función actual. También realiza una serie de otras optimizaciones en las asignaciones, como eliminar asignaciones que nunca se utilizan, optimizar llamadas typeof a objetos recién asignados y eliminar almacenes a asignaciones que son sobrescritas inmediatamente. La implementación del análisis de escape se encuentra en `llvm-alloc-helpers.cpp`. Actualmente, este pase no utiliza información de `EscapeAnalysis.jl`, aunque eso puede cambiar en el futuro.

### PropagateJuliaAddrspaces

  * Nombre de archivo: `llvm-propagate-addrspaces.cpp`
  * Nombre de la clase: `PropagateJuliaAddrspacesPass`
  * Nombre de la opción: `function(PropagateJuliaAddrspaces)`

Este pase se utiliza para propagar espacios de direcciones específicos de Julia a través de operaciones en punteros. LLVM no tiene permitido introducir o eliminar instrucciones addrspacecast mediante optimizaciones, por lo que este pase actúa para eliminar conversiones addrspace redundantes al reemplazar operaciones con su equivalente en un espacio de direcciones de Julia. Para más información sobre los espacios de direcciones de Julia, consulte (TODO enlace a llvm.md).

### JuliaLICM

  * Nombre de archivo: `llvm-julia-licm.cpp`
  * Nombre de la clase: `JuliaLICMPass`
  * Nombre de la opción: `loop(JuliaLICM)`

Este pase se utiliza para elevar intrínsecos específicos de Julia fuera de los bucles. Específicamente, realiza las siguientes transformaciones:

1. Elevar `gc_preserve_begin` y hundir `gc_preserve_end` fuera de los bucles cuando los objetos preservados son invariantes del bucle.

    1. Dado que los objetos preservados dentro de un bucle probablemente se preserven durante la duración del bucle, esta transformación puede reducir el número de pares `gc_preserve_begin`/`gc_preserve_end` en el IR. Esto facilita que el `LateLowerGCPass` identifique dónde se preservan objetos particulares.
2. Levantar barreras de escritura con objetos invariantes

    1. Aquí asumimos que solo hay dos generaciones de las que un objeto puede ser parte. Dado eso, una barrera de escritura necesita ejecutarse solo una vez para cualquier par del mismo objeto. Por lo tanto, podemos elevar las barreras de escritura fuera de los bucles cuando el objeto al que se está escribiendo es invariante en el bucle.
3. Elevar las asignaciones fuera de los bucles cuando no escapan del bucle

    1. Usamos una definición muy conservadora de escape aquí, la misma que se utiliza en `AllocOptPass`. Esta transformación puede reducir el número de asignaciones en el IR, incluso cuando una asignación escapa completamente de la función.

!!! note
    Este pase es necesario para preservar el [MemorySSA](https://llvm.org/docs/MemorySSA.html) ([Short Video](https://www.youtube.com/watch?v=bdxWmryoHak), [Longer Video](https://www.youtube.com/watch?v=1e5y6WDbXCQ)) y [ScalarEvolution](https://baziotis.cs.illinois.edu/compilers/introduction-to-scalar-evolution.html) ([Newer Slides](https://llvm.org/devmtg/2018-04/slides/Absar-ScalarEvolution.pdf) [Older Slides](https://llvm.org/devmtg/2009-10/ScalarEvolutionAndLoopOptimization.pdf)) análisis.

