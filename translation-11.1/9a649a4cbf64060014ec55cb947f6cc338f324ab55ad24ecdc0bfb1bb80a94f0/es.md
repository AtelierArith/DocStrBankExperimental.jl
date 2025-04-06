# JIT Design and Implementation

Este documento explica el diseño e implementación del JIT de Julia, después de que la generación de código ha finalizado y se ha producido IR de LLVM no optimizado. El JIT es responsable de optimizar y compilar este IR a código de máquina, y de enlazarlo en el proceso actual y hacer que el código esté disponible para su ejecución.

## Introduction

El JIT es responsable de gestionar los recursos de compilación, buscar código previamente compilado y compilar nuevo código. Está construido principalmente sobre la tecnología [On-Request-Compilation](https://llvm.org/docs/ORCv2.html) (ORCv2) de LLVM, que proporciona soporte para una serie de características útiles, como la compilación concurrente, la compilación perezosa y la capacidad de compilar código en un proceso separado. Aunque LLVM proporciona un compilador JIT básico en forma de LLJIT, Julia utiliza muchas API de ORCv2 directamente para crear su propio compilador JIT personalizado.

## Overview

![Diagrama del flujo del compilador](./img/compiler_diagram.png)

Codegen produce un módulo LLVM que contiene IR para una o más funciones de Julia a partir del IR SSA original de Julia producido por la inferencia de tipos (etiquetado como translate en el diagrama del compilador anterior). También produce un mapeo de instancia de código a nombre de función LLVM. Sin embargo, aunque se han aplicado algunas optimizaciones por el compilador basado en Julia en el IR de Julia, el IR de LLVM producido por codegen aún contiene muchas oportunidades para optimización. Así, el primer paso que toma el JIT es ejecutar una tubería de optimización independiente del objetivo[^tdp] en el módulo LLVM. Luego, el JIT ejecuta una tubería de optimización dependiente del objetivo, que incluye optimizaciones específicas del objetivo y generación de código, y produce un archivo objeto. Finalmente, el JIT vincula el archivo objeto resultante en el proceso actual y hace que el código esté disponible para su ejecución. Todo esto está controlado por código en `src/jitlayers.cpp`.

[^tdp]: This is not a totally-target independent pipeline, as transformations such as vectorization rely upon target information such as vector register width and cost modeling. Additionally, codegen itself makes a few target-dependent assumptions, and the optimization pipeline will take advantage of that knowledge.

Actualmente, solo se permite que un hilo a la vez ingrese al pipeline de optimización-compilación-enlace, debido a las restricciones impuestas por uno de nuestros enlazadores (RuntimeDyld). Sin embargo, el JIT está diseñado para soportar la optimización y compilación concurrentes, y se espera que la restricción del enlazador se levante en el futuro cuando RuntimeDyld haya sido completamente reemplazado en todas las plataformas.

## Optimization Pipeline

El pipeline de optimización se basa en el nuevo administrador de pases de LLVM, pero el pipeline está personalizado para las necesidades de Julia. El pipeline se define en `src/pipeline.cpp`, y en términos generales avanza a través de una serie de etapas como se detalla a continuación.

1. Simplificación Temprana

    1. Estos pases se utilizan principalmente para simplificar el IR y canonizar patrones para que los pases posteriores puedan identificar esos patrones más fácilmente. Además, varias llamadas intrínsecas, como sugerencias de predicción de ramas y anotaciones, se reducen a otros metadatos u otras características del IR. [`SimplifyCFG`](https://llvm.org/docs/Passes.html#simplifycfg-simplify-the-cfg) (simplificar el grafo de control de flujo), [`DCE`](https://llvm.org/docs/Passes.html#dce-dead-code-elimination) (eliminación de código muerto) y [`SROA`](https://llvm.org/docs/Passes.html#sroa-scalar-replacement-of-aggregates) (reemplazo escalar de agregados) son algunos de los actores clave aquí.
2. Optimización temprana

    1. Estos pases son típicamente baratos y se centran principalmente en reducir el número de instrucciones en el IR y propagar conocimiento a otras instrucciones. Por ejemplo, [`EarlyCSE`](https://en.wikipedia.org/wiki/Common_subexpression_elimination) se utiliza para realizar la eliminación de subexpresiones comunes, y [`InstCombine`](https://llvm.org/docs/Passes.html#instcombine-combine-redundant-instructions) y [`InstSimplify`](https://llvm.org/doxygen/classllvm_1_1InstSimplifyPass.html#details) realizan una serie de pequeñas optimizaciones de mirilla para hacer que las operaciones sean menos costosas.
3. Optimización de bucles

    1. Estos pases canonizan y simplifican bucles. Los bucles son a menudo código caliente, lo que hace que la optimización de bucles sea extremadamente importante para el rendimiento. Los actores clave aquí incluyen [`LoopRotate`](https://llvm.org/docs/Passes.html#loop-rotate-rotate-loops), [`LICM`](https://llvm.org/docs/Passes.html#licm-loop-invariant-code-motion), y [`LoopFullUnroll`](https://llvm.org/docs/Passes.html#loop-unroll-unroll-loops). También ocurre cierta eliminación de comprobaciones de límites aquí, como resultado del pase [`IRCE`](https://llvm.org/doxygen/InductiveRangeCheckElimination_8cpp_source.html) que puede demostrar que ciertos límites nunca se exceden.
4. Optimización Escalar

    1. El pipeline de optimización escalar contiene una serie de pasos más costosos, pero más poderosos, como [`GVN`](https://llvm.org/docs/Passes.html#gvn-global-value-numbering) (numeración de valores globales), [`SCCP`](https://llvm.org/docs/Passes.html#sccp-sparse-conditional-constant-propagation) (propagación de constantes condicionales dispersas), y otra ronda de eliminación de comprobaciones de límites. Estos pasos son costosos, pero a menudo pueden eliminar grandes cantidades de código y hacer que la vectorización sea mucho más exitosa y efectiva. Varios otros pasos de simplificación y optimización se intercalan con los más costosos para reducir la cantidad de trabajo que tienen que hacer.
5. Vectorización

    1. [Automatic vectorization](https://en.wikipedia.org/wiki/Automatic_vectorization) es una transformación extremadamente poderosa para código intensivo en CPU. Brevemente, la vectorización permite la ejecución de una [single instruction on multiple data](https://en.wikipedia.org/wiki/Single_instruction,_multiple_data) (SIMD), por ejemplo, realizar 8 operaciones de suma al mismo tiempo. Sin embargo, demostrar que el código es tanto capaz de vectorización como rentable para vectorizar es difícil, y esto depende en gran medida de las pasadas de optimización previas para transformar el IR en un estado donde la vectorización valga la pena.
6. Bajada Intrínseca

    1. Julia inserta una serie de intrínsecos personalizados, por razones como la asignación de objetos, la recolección de basura y el manejo de excepciones. Estos intrínsecos se colocaron originalmente para hacer que las oportunidades de optimización fueran más obvias, pero ahora se reducen a IR de LLVM para permitir que el IR se emita como código de máquina.
7. Limpieza

    1. Estas optimizaciones de pases son de última oportunidad y realizan pequeñas optimizaciones como la propagación de multiplicación-adición fusionada y la simplificación de división-resto. Además, los objetivos que no admiten números de punto flotante de media precisión tendrán sus instrucciones de media precisión convertidas en instrucciones de precisión simple aquí, y se añaden pases para proporcionar soporte de sanitizador.

## Target-Dependent Optimization and Code Generation

LLVM proporciona optimización dependiente del objetivo y generación de código máquina en el mismo pipeline, ubicado en el TargetMachine para una plataforma dada. Estos pases incluyen selección de instrucciones, programación de instrucciones, asignación de registros y emisión de código máquina. La documentación de LLVM ofrece una buena visión general del proceso, y el código fuente de LLVM es el mejor lugar para buscar detalles sobre el pipeline y los pases.

## Linking

Actualmente, Julia está en transición entre dos enlazadores: el antiguo enlazador RuntimeDyld y el nuevo enlazador [JITLink](https://llvm.org/docs/JITLink.html). JITLink contiene una serie de características que RuntimeDyld no tiene, como el enlace concurrente y reentrante, pero actualmente carece de un buen soporte para integraciones de perfilado y aún no soporta todas las plataformas que RuntimeDyld soporta. Con el tiempo, se espera que JITLink reemplace completamente a RuntimeDyld. Se pueden encontrar más detalles sobre JITLink en la documentación de LLVM.

## Execution

Una vez que el código ha sido vinculado al proceso actual, está disponible para su ejecución. Este hecho se hace saber al código generador mediante la actualización de los campos `invoke`, `specsigflags` y `specptr` de manera apropiada. Los codeinsts admiten la actualización de los campos `invoke`, `specsigflags` y `specptr`, siempre que cada combinación de estos campos que exista en un momento dado sea válida para ser llamada. Esto permite que el JIT actualice estos campos sin invalidar los codeinsts existentes, apoyando un posible JIT concurrente en el futuro. Específicamente, los siguientes estados pueden ser válidos:

1. `invoke` es NULL, `specsigflags` es 0b00, `specptr` es NULL

    1. Este es el estado inicial de un codeinst, e indica que el codeinst aún no ha sido compilado.
2. `invoke` no es nulo, `specsigflags` es 0b00, `specptr` es NULL

    1. Esto indica que el codeinst no fue compilado con ninguna especialización, y que el codeinst debe ser invocado directamente. Tenga en cuenta que en este caso, `invoke` no lee ni los campos `specsigflags` ni `specptr`, y por lo tanto, pueden ser modificados sin invalidar el puntero `invoke`.
3. `invoke` no es nulo, `specsigflags` es 0b10, `specptr` no es nulo

    1. Esto indica que el codeinst fue compilado, pero se consideró innecesaria una firma de función especializada por parte de codegen.
4. `invoke` no es nulo, `specsigflags` es 0b11, `specptr` no es nulo

    1. Esto indica que el codeinst fue compilado y se consideró necesario un firma de función especializada por parte de codegen. El campo `specptr` contiene un puntero a la firma de función especializada. Se permite que el puntero `invoke` lea tanto los campos `specsigflags` como `specptr`.

Además, hay una serie de diferentes estados transitorios que ocurren durante el proceso de actualización. Para tener en cuenta estas situaciones potenciales, se deben utilizar los siguientes patrones de escritura y lectura al tratar con estos campos de codeinst.

1. Al escribir `invoke`, `specsigflags` y `specptr`:

    1. Realiza una operación de comparación e intercambio atómico de `specptr` asumiendo que el valor antiguo era NULL. Esta operación de comparación e intercambio debe tener al menos un orden de adquisición-liberación, para proporcionar garantías de orden de las operaciones de memoria restantes en la escritura.
    2. Si `specptr` no era nulo, cesar la operación de escritura y esperar a que el bit 0b10 de `specsigflags` sea escrito.
    3. Escribe el nuevo bit bajo de `specsigflags` a su valor final. Esto puede ser una escritura relajada.
    4. Escribe el nuevo puntero `invoke` a su valor final. Esto debe tener al menos un orden de memoria de liberación para sincronizarse con las lecturas de `invoke`.
    5. Establezca el segundo bit de `specsigflags` en 1. Esto debe ser al menos un orden de memoria de liberación para sincronizarse con las lecturas de `specsigflags`. Este paso completa la operación de escritura y anuncia a todos los demás hilos que todos los campos han sido establecidos.
2. Al leer todos los `invoke`, `specsigflags` y `specptr`:

    1. Lee el campo `invoke` con al menos un orden de memoria de adquisición. Esta carga se denominará `initial_invoke`.
    2. Si `initial_invoke` es NULL, el codeinst aún no es ejecutable. `invoke` es NULL, `specsigflags` puede ser tratado como 0b00, `specptr` puede ser tratado como NULL.
    3. Lee el campo `specptr` con al menos un orden de memoria de adquisición.
    4. Si `specptr` es NULL, entonces el puntero `initial_invoke` no debe depender de `specptr` para garantizar una ejecución correcta. Por lo tanto, `invoke` es no nulo, `specsigflags` puede ser tratado como 0b00, `specptr` puede ser tratado como NULL.
    5. Si `specptr` no es nulo, entonces `initial_invoke` podría no ser el campo final `invoke` que utiliza `specptr`. Esto puede ocurrir si `specptr` ha sido escrito, pero `invoke` aún no ha sido escrito. Por lo tanto, gira en el segundo bit de `specsigflags` hasta que se establezca en 1 con al menos un orden de memoria de adquisición.
    6. Vuelve a leer el campo `invoke` con al menos un orden de memoria de adquisición. Esta carga se referirá como `final_invoke`.
    7. Lee el campo `specsigflags` con cualquier orden de memoria.
    8. `invoke` es `final_invoke`, `specsigflags` es el valor leído en el paso 7, `specptr` es el valor leído en el paso 3.
3. Al actualizar un `specptr` a un puntero de función diferente pero equivalente:

    1. Realice un almacenamiento de liberación del nuevo puntero de función a `specptr`. Las condiciones de carrera aquí deben ser benignas, ya que el antiguo puntero de función debe seguir siendo válido, y cualquier nuevo también debe ser válido. Una vez que se ha escrito un puntero en `specptr`, debe ser siempre invocable, ya sea que se sobrescriba más tarde o no.

Aunque estos pasos de escritura, lectura y actualización son complicados, garantizan que el JIT pueda actualizar codeinsts sin invalidar los codeinsts existentes, y que el JIT pueda actualizar codeinsts sin invalidar los punteros `invoke` existentes. Esto permite que el JIT pueda reoptimizar potencialmente funciones a niveles de optimización más altos en el futuro, y también permitirá que el JIT soporte la compilación concurrente de funciones en el futuro.
