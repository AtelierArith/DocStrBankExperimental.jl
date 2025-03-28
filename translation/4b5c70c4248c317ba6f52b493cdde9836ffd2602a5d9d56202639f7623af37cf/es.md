# Garbage Collection in Julia

## Introduction

Julia tiene un recolector de basura de marcado y barrido que no se mueve, es parcialmente concurrente, paralelo, generacional y mayormente preciso (se proporciona una interfaz para el escaneo conservador de pilas como una opción para los usuarios que deseen llamar a Julia desde C).

## Allocation

Julia utiliza dos tipos de asignadores, siendo el tamaño de la solicitud de asignación el que determina cuál se utiliza. Los objetos de hasta 2k bytes se asignan en un asignador de lista libre por hilo, mientras que los objetos de más de 2k bytes se asignan a través de libc malloc.

El asignador de memoria de Julia particiona objetos en diferentes clases de tamaño, de modo que una página de memoria gestionada por el asignador de memoria (que abarca 4 páginas del sistema operativo en plataformas de 64 bits) solo contiene objetos de la misma clase de tamaño. Cada página de memoria del asignador de memoria se empareja con algunos metadatos de página almacenados en listas libres sin bloqueo por hilo. Los metadatos de la página contienen información como si la página tiene objetos vivos en absoluto, el número de espacios libres y los desplazamientos al primer y último objeto en la lista de libres contenida en esa página. Estos metadatos se utilizan para optimizar la fase de recolección: una página que no tiene objetos vivos en absoluto puede ser devuelta al sistema operativo sin necesidad de escanearla, por ejemplo.

Mientras que una página que no tiene objetos puede ser devuelta al sistema operativo, su metadata asociada está permanentemente asignada y puede sobrevivir a la página dada. Como se mencionó anteriormente, la metadata para las páginas asignadas se almacena en listas libres de bloqueo por hilo. Sin embargo, la metadata para las páginas libres puede almacenarse en tres listas separadas libres de bloqueo dependiendo de si la página ha sido mapeada pero nunca accedida (`page_pool_clean`), o si la página ha sido barrida de manera perezosa y está esperando ser aconsejada por un hilo de GC en segundo plano (`page_pool_lazily_freed`), o si la página ha sido aconsejada (`page_pool_freed`).

El asignador de memoria de Julia sigue una disciplina de asignación "por niveles". Al solicitar una página de memoria para el asignador de memoria, Julia:

  * Intenta reclamar una página de `page_pool_lazily_freed`, que contiene páginas que estaban vacías en la última fase de detener el mundo, pero que aún no han sido madividas por un hilo de recolección de basura concurrente.
  * Si falló al reclamar una página de `page_pool_lazily_freed`, intentará reclamar una página de `the page_pool_clean`, que contiene páginas que fueron mmaped en una solicitud de asignación de página anterior pero que nunca fueron accedidas.
  * Si falló al reclamar una página de `pool_page_clean` y de `page_pool_lazily_freed`, intentará reclamar una página de `page_pool_freed`, que contiene páginas que ya han sido aconsejadas por un hilo de recolección de basura (GC) concurrente y cuya dirección virtual subyacente puede ser reciclada.
  * Si falló en todos los intentos mencionados anteriormente, asignará un lote de páginas, reclamará una página para sí mismo e insertará las páginas restantes en `page_pool_clean`.

![Diagrama de asignación de piscina en niveles](./img/gc-tiered-allocation.jpg)

## Marking and Generational Collection

La fase de marcado de Julia se implementa a través de una búsqueda en profundidad iterativa paralela sobre el grafo de objetos. El recolector de Julia es no móvil, por lo que la información sobre la edad del objeto no se puede determinar solo a través de la región de memoria en la que reside el objeto, sino que debe estar de alguna manera codificada en el encabezado del objeto o en una tabla auxiliar. Los dos bits más bajos del encabezado de un objeto se utilizan para almacenar, respectivamente, un bit de marcado que se establece cuando un objeto se escanea durante la fase de marcado y un bit de edad para la recolección generacional.

La recolección generacional se implementa a través de bits adhesivos: los objetos solo se empujan a la pila de marcas y, por lo tanto, se rastrean, si sus bits de marca no están establecidos. Cuando los objetos alcanzan la generación más antigua, sus bits de marca no se restablecen durante el llamado "barrido rápido", lo que lleva a que estos objetos no sean rastreados en una fase de marca subsiguiente. Sin embargo, un "barrido completo" provoca que los bits de marca de todos los objetos se restablezcan, lo que lleva a que todos los objetos sean rastreados en una fase de marca subsiguiente. Los objetos se promueven a la siguiente generación durante cada fase de barrido que sobreviven. En el lado del mutador, las escrituras de campo se interceptan a través de una barrera de escritura que empuja la dirección de un objeto a un conjunto recordado por hilo si el objeto está en la última generación, y si el objeto en el campo que se está escribiendo no lo está. Los objetos en este conjunto recordado se rastrean durante la fase de marca.

## Sweeping

La limpieza de grupos de objetos en Julia puede caer en dos categorías: si una página dada gestionada por el asignador de grupos contiene al menos un objeto vivo, entonces se debe enlazar una lista de libres a través de sus objetos muertos; si una página dada no contiene objetos vivos en absoluto, entonces su memoria física subyacente puede ser devuelta al sistema operativo a través, por ejemplo, del uso de llamadas al sistema madvise en Linux.

La primera categoría de barrido se paraleliza a través del robo de trabajo. Para la segunda categoría de barrido, si el barrido de páginas concurrente está habilitado a través de la bandera `--gcthreads=X,1`, realizamos las llamadas al sistema madvise en un hilo de barrido en segundo plano, de manera concurrente con los hilos mutadores. Durante la fase de detener el mundo del recolector, las páginas asignadas en el pool que no contienen objetos vivos se empujan inicialmente en `pool_page_lazily_freed`. Luego, se despierta el hilo de barrido en segundo plano, que es responsable de eliminar páginas de `pool_page_lazily_freed`, llamar a madvise sobre ellas e insertarlas en `pool_page_freed`. Como se describió anteriormente, `pool_page_lazily_freed` también se comparte con los hilos mutadores. Esto implica que en cargas de trabajo multihilo con alta asignación, los hilos mutadores a menudo evitarían una falta de página en la asignación (proveniente del acceso a una página mmaped fresca o al acceso a una página madvised) al asignar directamente desde una página en `pool_page_lazily_freed`, mientras que el hilo de barrido en segundo plano necesita madvise un número reducido de páginas dado que algunas de ellas ya fueron reclamadas por los mutadores.

## Heuristics

Las heurísticas de GC ajustan el GC al cambiar el tamaño del intervalo de asignación entre las recolecciones de basura.

Las heurísticas de GC miden cuán grande es el tamaño del heap después de una recolección y establecen la próxima recolección de acuerdo con el algoritmo descrito en https://dl.acm.org/doi/10.1145/3563323. En resumen, argumenta que el objetivo del heap debería tener una relación de raíz cuadrada con el heap vivo, y que también debería escalarse según la rapidez con la que el GC libera objetos y la rapidez con la que los mutadores están asignando. Las heurísticas miden el tamaño del heap contando el número de páginas que están en uso y los objetos que utilizan malloc. Anteriormente, medíamos el tamaño del heap contando los objetos vivos, pero eso no toma en cuenta la fragmentación, lo que podría llevar a malas decisiones; eso también significaba que utilizábamos información local de hilos (asignaciones) para tomar decisiones sobre un proceso en general (cuándo hacer GC), medir páginas significa que la decisión es global.

El GC realizará colecciones completas cuando el tamaño del heap alcance el 80% del tamaño máximo permitido.
