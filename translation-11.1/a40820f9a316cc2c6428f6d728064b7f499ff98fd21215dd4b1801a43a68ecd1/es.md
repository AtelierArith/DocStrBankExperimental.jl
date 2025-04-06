# [Proper maintenance and care of multi-threading locks](@id Proper-maintenance-and-care-of-multi-threading-locks)

Las siguientes estrategias se utilizan para garantizar que el código esté libre de interbloqueos (generalmente abordando la cuarta condición de Coffman: espera circular).

> 1. estructura el código de tal manera que solo se necesite adquirir un bloqueo a la vez
> 2. siempre adquiera bloqueos compartidos en el mismo orden, según lo indicado en la tabla a continuación
> 3. evitar construcciones que esperen necesitar recursión sin restricciones


## Locks

A continuación se presentan todas las cerraduras que existen en el sistema y los mecanismos para utilizarlas que evitan el potencial de interbloqueos (no se permite el algoritmo del avestruz aquí):

Los siguientes son definitivamente bloqueos de hoja (nivel 1) y no deben intentar adquirir ningún otro bloqueo:

>   * punto seguro
>
>     > Tenga en cuenta que este bloqueo se adquiere implícitamente mediante `JL_LOCK` y `JL_UNLOCK`. Use las variantes `_NOGC` para evitar eso en bloqueos de nivel 1.
>     >
>     > Mientras se sostiene este bloqueo, el código no debe realizar ninguna asignación ni alcanzar ningún punto seguro. Tenga en cuenta que hay puntos seguros al realizar asignaciones, habilitar / deshabilitar la recolección de basura, entrar / restaurar marcos de excepciones y tomar / liberar bloqueos.
>   * mapa_compartido
>   * finalizadores
>   * pagealloc
>   * gc*perm*lock
>   * flisp
>   * jl*en*stackwalk (Win32)
>   * ResourcePool<?>::mutex
>   * RLST_mutex
>   * llvm*imprimiendo*mutex
>   * jl*bloqueado*stream::mutex
>   * debuginfo_asyncsafe
>   * inferencia*tiempo*mutex
>   * ExecutionEngine::SessionLock
>
>     > flisp en sí mismo ya es seguro para hilos, este bloqueo solo protege el grupo `jl_ast_context_list_t`, de igual manera, los mutexes de ResourcePool<?>::solo protegen el grupo de recursos asociado.


El siguiente es un bloqueo de hoja (nivel 2), y solo adquiere bloqueos de nivel 1 (punto seguro) internamente:

>   * global*roots*lock
>   * Módulo->bloquear
>   * JLDebuginfoPlugin::PluginMutex
>   * nuevo*inferido*mutex


El siguiente es un candado de nivel 3, que solo puede adquirir candados de nivel 1 o nivel 2 internamente:

>   * Método->bloqueoEscritura
>   * tipo de caché


El siguiente es un candado de nivel 4, que solo puede recurrir para adquirir candados de nivel 1, 2 o 3:

>   * MethodTable->bloqueoEscritura


No se puede llamar a ningún código de Julia mientras se sostiene un bloqueo por encima de este punto.

orc::ThreadSafeContext (TSCtx) los bloqueos ocupan un lugar especial en la jerarquía de bloqueos. Se utilizan para proteger el estado global no seguro para hilos de LLVM, pero puede haber un número arbitrario de ellos. Por defecto, todos estos bloqueos pueden ser tratados como bloqueos de nivel 5 a efectos de comparación con el resto de la jerarquía. La adquisición de un TSCtx solo debe hacerse desde el grupo de TSCtx del JIT, y todos los bloqueos en ese TSCtx deben ser liberados antes de devolverlo al grupo. Si se deben adquirir múltiples bloqueos de TSCtx al mismo tiempo (debido a la compilación recursiva), entonces los bloqueos deben adquirirse en el orden en que los TSCtx fueron tomados del grupo.

El siguiente es un candado de nivel 5.

>   * JuliaOJIT::EmissionMutex


El siguiente es un candado de nivel 6, que solo puede recurrir para adquirir candados en niveles inferiores:

>   * código generador
>   * jl*modules*mutex


Lo siguiente es un bloqueo casi raíz (nivel final-1), lo que significa que solo se puede mantener el bloqueo raíz al intentar adquirirlo:

>   * typeinf
>
>     > este quizás sea uno de los más complicados, ya que la inferencia de tipos puede ser invocada desde muchos puntos
>     >
>     > actualmente el bloqueo está fusionado con el bloqueo de codegen, ya que se llaman entre sí de forma recursiva


El siguiente bloqueo sincroniza la operación de E/S. Ten en cuenta que realizar cualquier E/S (por ejemplo, imprimir mensajes de advertencia o información de depuración) mientras se sostiene cualquier otro bloqueo mencionado anteriormente puede resultar en bloqueos perniciosos y difíciles de encontrar. ¡TEN MUCHO CUIDADO!

>   * iolock
>   * Bloqueos de ThreadSynchronizers individuales
>
>     > esto puede continuar realizándose después de liberar el iolock, o adquirirse sin él, pero ten mucho cuidado de nunca intentar adquirir el iolock mientras lo sostienes
>   * Libdl.LazyLibrary bloqueo


La siguiente es la cerradura raíz, lo que significa que no se debe tener ninguna otra cerradura al intentar adquirirla:

>   * nivel superior
>
>     > esto debe llevarse a cabo al intentar una acción de alto nivel (como crear un nuevo tipo o definir un nuevo método): intentar obtener este bloqueo dentro de una función en etapa causará una condición de interbloqueo.
>     >
>     > además, no está claro si *cualquier* código puede ejecutarse de manera segura en paralelo con una expresión de nivel superior arbitraria, por lo que puede requerir que todos los hilos lleguen primero a un punto seguro.


## Broken Locks

Las siguientes cerraduras están rotas:

  * nivel superior

    > no existe en este momento
    >
    > arreglar: créalo
  * Módulo->bloquear

    > Esto es vulnerable a bloqueos ya que no puede estar seguro de que se adquiera en secuencia. Algunas operaciones (como `import_module`) carecen de un bloqueo.
    >
    > arreglar: reemplazar con `jl_modules_mutex`?
  * loading.jl: `require` y `register_root_module`

    > Este archivo potencialmente tiene numerosos problemas.
    >
    > arreglar: necesita cerraduras

## Shared Global Data Structures

Estas estructuras de datos necesitan bloqueos debido a que son un estado global mutable compartido. Es la lista inversa de la lista de prioridad de bloqueos anterior. Esta lista no incluye recursos hoja de nivel 1 debido a su simplicidad.

Modificaciones de MethodTable (def, cache) : MethodTable->bloqueo de escritura

Declaraciones de tipo: bloqueo de nivel superior

Tipo de aplicación: bloqueo de caché de tipo

Tablas de variables globales: Módulo->bloquear

Módulo serializador: bloqueo de nivel superior

JIT y inferencia de tipos: bloqueo de generación de código

Actualizaciones de MethodInstance/CodeInstance: Method->writelock, bloqueo de codegen

>   * Estos se establecen en la construcción e son inmutables:
>
>       * tiposDeEspecificación
>       * sparam_vals
>       * def
>       * propietario


>   * Estos son establecidos por `jl_type_infer` (mientras se mantiene el bloqueo de generación de código):
>
>       * caché
>       * rettype
>       * inferido


```
    * valid ages
```

>   * `inInference` bandera:
>
>       * optimización para evitar rápidamente volver a `jl_type_infer` mientras ya se está ejecutando
>       * el estado actual (de establecer `inferred`, luego `fptr`) está protegido por el bloqueo de generación de código


>   * Punteros a funciones:
>
>       * estas transiciones ocurren una vez, de `NULL` a un valor, mientras se mantiene el bloqueo de generación de código
>   * Caché del generador de código (el contenido de `functionObjectsDecls`):
>
>       * estos pueden transitar múltiples veces, pero solo mientras se mantenga el bloqueo de generación de código
>       * es válido usar una versión antigua de esto, o bloquear para nuevas versiones de esto, por lo que las carreras son benignas, siempre que el código tenga cuidado de no hacer referencia a otros datos en la instancia del método (como `rettype`) y asuma que está coordinado, a menos que también se mantenga el bloqueo de generación de código.


LLVMContext : bloqueo de generación de código

Método : Método->bloqueoEscritura

  * raíces matriz (serializador y generación de código)
  * invocar / especializaciones / modificaciones de tfunc
