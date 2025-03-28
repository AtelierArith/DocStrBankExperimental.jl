# Ahead of Time Compilation

Este documento describe el diseño y la estructura del sistema de compilación anticipada (AOT) en Julia. Este sistema se utiliza al generar imágenes del sistema e imágenes de paquetes. Gran parte de la implementación descrita aquí se encuentra en `aotcompile.cpp`, `staticdata.c` y `processor.cpp`.

## Introduction

Aunque Julia normalmente compila el código justo a tiempo (JIT), es posible compilar el código por adelantado y guardar el código resultante en un archivo. Esto puede ser útil por varias razones:

1. Para reducir el tiempo que tarda en iniciar un proceso de Julia.
2. Para reducir el tiempo dedicado al compilador JIT en lugar de ejecutar código (tiempo hasta la primera ejecución, TTFX).
3. Para reducir la cantidad de memoria utilizada por el compilador JIT.

## High-Level Overview

Las siguientes descripciones son una instantánea de los detalles de implementación actuales del pipeline de extremo a extremo que ocurre internamente cuando el usuario compila un nuevo módulo AOT, como sucede cuando escribe `using Foo`. Es probable que estos detalles cambien con el tiempo a medida que implementemos mejores formas de manejarlos, por lo que las implementaciones actuales pueden no coincidir exactamente con el flujo de datos y las funciones descritas a continuación.

### Compiling Code Images

Primero, se deben identificar los métodos que necesitan ser compilados a código nativo. Esto solo se puede hacer ejecutando realmente el código que se va a compilar, ya que el conjunto de métodos que necesitan ser compilados depende de los tipos de los argumentos pasados a los métodos, y las invocaciones de métodos con ciertas combinaciones de tipos pueden no ser conocidas hasta el tiempo de ejecución. Durante este proceso, se rastrean los métodos exactos que el compilador ve para una compilación posterior, produciendo un rastro de compilación.

!!! note
    Actualmente, al compilar imágenes, Julia ejecuta la generación de trazas en un proceso diferente al proceso que realiza la compilación AOT. Esto puede tener impactos al intentar usar un depurador durante la precompilación. La mejor manera de depurar la precompilación con un depurador es usar el depurador rr, grabar todo el árbol de procesos, usar `rr ps` para identificar el proceso fallido relevante y luego usar `rr replay -p PID` para reproducir solo el proceso fallido.


Una vez que se han identificado los métodos que se van a compilar, se pasan a la función `jl_create_system_image`. Esta función configura una serie de estructuras de datos que se utilizarán al serializar el código nativo en un archivo, y luego llama a `jl_create_native` con el array de métodos. `jl_create_native` ejecuta la generación de código en los métodos y produce uno o más módulos de LLVM. Luego, `jl_create_system_image` registra información útil sobre lo que la generación de código produjo a partir del(los) módulo(s).

Los módulos se pasan luego a `jl_dump_native`, junto con la información registrada por `jl_create_system_image`. `jl_dump_native` contiene el código necesario para serializar los módulos a bitcode, archivos de objeto o archivos de ensamblaje, dependiendo de las opciones de línea de comandos pasadas a Julia. El código serializado y la información se escriben luego en un archivo como un archivo comprimido.

El paso final es ejecutar un enlazador de sistema en los archivos objeto en el archivo producido por `jl_dump_native`. Una vez que este paso esté completo, se produce una biblioteca compartida que contiene el código compilado.

### Loading Code Images

Al cargar una imagen de código, la biblioteca compartida producida por el enlazador se carga en la memoria. Luego, los datos de la imagen del sistema se cargan desde la biblioteca compartida. Estos datos contienen información sobre los tipos, métodos e instancias de código que se compilaron en la biblioteca compartida. Estos datos se utilizan para restaurar el estado del tiempo de ejecución a lo que era cuando se compiló la imagen de código.

Si la imagen de código se compiló con multiversionado, el cargador seleccionará la versión apropiada de cada función para usar según las características de la CPU disponibles en la máquina actual.

Para las imágenes del sistema, dado que no se ha cargado ningún otro código, el estado del tiempo de ejecución es ahora el mismo que cuando se compiló la imagen de código. Para las imágenes de paquetes, el entorno puede haber cambiado en comparación con cuando se compiló el código, por lo que cada método debe ser verificado contra la tabla de métodos global para determinar si sigue siendo un código válido.

## Compiling Methods

### Tracing Compiled Methods

Julia tiene una opción de línea de comandos para registrar todos los métodos que son compilados por el compilador JIT, `--trace-compile=filename`. Cuando una función es compilada y esta opción tiene un nombre de archivo, Julia imprimirá una declaración de precompilación en ese archivo con el método y los tipos de argumentos con los que fue llamada. Esto genera, por lo tanto, un script de precompilación que se puede utilizar más tarde en el proceso de compilación AOT. El paquete [PrecompileTools](https://julialang.github.io/PrecompileTools.jl/stable/) tiene herramientas que pueden facilitar el aprovechamiento de esta funcionalidad para los desarrolladores de paquetes.

### `jl_create_system_image`

`jl_create_system_image` guarda todos los metadatos específicos de Julia necesarios para restaurar más tarde el estado del tiempo de ejecución. Esto incluye datos como instancias de código, instancias de métodos, tablas de métodos e información de tipos. Esta función también configura las estructuras de datos necesarias para serializar el código nativo en un archivo. Finalmente, llama a `jl_create_native` para crear uno o más módulos LLVM que contienen el código nativo para los métodos que se le pasaron. `jl_create_native` es responsable de ejecutar la generación de código en los métodos que se le pasaron.

### `jl_dump_native`

`jl_dump_native` es responsable de serializar el módulo LLVM que contiene el código nativo a un archivo. Además del módulo, los datos de la imagen del sistema producidos por `jl_create_system_image` se compilan como una variable global. La salida de este método es bitcode, objetos y/o archivos de ensamblaje que contienen el código y los datos de la imagen del sistema.

`jl_dump_native` es típicamente uno de los mayores consumos de tiempo al emitir código nativo, con gran parte del tiempo dedicado a optimizar LLVM IR y emitir código de máquina. Por lo tanto, esta función es capaz de multihilo en los pasos de optimización y emisión de código de máquina. Este multihilo está parametrizado en el tamaño del módulo, pero se puede anular explícitamente configurando la variable de entorno [`JULIA_IMAGE_THREADS`](@ref JULIA_IMAGE_THREADS). El número máximo de hilos por defecto es la mitad del número de hilos disponibles, pero configurarlo para que sea menor puede reducir el uso máximo de memoria durante la compilación.

`jl_dump_native` también puede producir código nativo optimizado para múltiples arquitecturas, cuando se integra con el cargador de Julia. Esto se activa configurando la variable de entorno [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) y mediado por el paso de multiversionado en la tubería de optimización. Para que esto funcione con multihilos, se añade un paso de anotación antes de que el módulo se divida en submódulos que se emiten en sus propios hilos, y este paso de anotación utiliza información disponible a lo largo de todo el módulo para decidir qué funciones se clonan para diferentes arquitecturas. Una vez que ha ocurrido la anotación, los hilos individuales pueden emitir código para diferentes arquitecturas en paralelo, sabiendo que un submódulo diferente está garantizado para producir las funciones necesarias que serán llamadas por una función clonada.

También se almacena en el archivo algunos otros metadatos sobre cómo se serializó el módulo, como el número de hilos utilizados para serializar el módulo y el número de funciones que se compilaron.

### Static Linking

El paso final en el proceso de compilación AOT es ejecutar un enlazador en los archivos objeto en el archivo producido por `jl_dump_native`. Esto produce una biblioteca compartida que contiene el código compilado. Esta biblioteca compartida puede ser cargada por Julia para restaurar el estado del tiempo de ejecución. Al compilar una imagen del sistema, se utiliza el enlazador nativo empleado por un compilador C para producir la biblioteca compartida final. Para las imágenes de paquetes, se utiliza el enlazador LLVM LLD para proporcionar una interfaz de enlace más consistente.

## Loading Code Images

### Loading the Shared Library

El primer paso para cargar una imagen de código es cargar la biblioteca compartida producida por el enlazador. Esto se hace llamando a `jl_dlopen` en la ruta de la biblioteca compartida. Esta función es responsable de cargar la biblioteca compartida y resolver todos los símbolos en la biblioteca.

### Loading Native Code

El cargador primero necesita identificar si el código nativo que fue compilado es válido para la arquitectura en la que se está ejecutando el cargador. Esto es necesario para evitar ejecutar instrucciones que las CPU más antiguas no reconocen. Esto se hace verificando las características de la CPU disponibles en la máquina actual en comparación con las características de la CPU para las que se compiló el código. Cuando se habilita la multiversión, el cargador seleccionará la versión apropiada de cada función para usar según las características de la CPU disponibles en la máquina actual. Si ninguno de los conjuntos de características que fueron multiversionados, el cargador generará un error.

Parte del pase de multiversionado crea una serie de arreglos globales de todas las funciones en el módulo. Cuando este proceso se ejecuta en múltiples hilos, se crea un arreglo de arreglos, que el cargador reorganiza en un gran arreglo con todas las funciones que fueron compiladas para esta arquitectura. Un proceso similar ocurre para las variables globales en el módulo.

### Setting Up Julia State

El cargador luego utiliza las variables y funciones globales producidas al cargar código nativo para configurar las estructuras de datos centrales del tiempo de ejecución de Julia en el proceso actual. Esta configuración implica agregar tipos y métodos al tiempo de ejecución de Julia, y hacer que el código nativo en caché esté disponible para su uso por otras funciones de Julia y el intérprete. Para las imágenes de paquetes, cada método debe ser validado, ya que el estado de la tabla de métodos global debe coincidir con el estado para el cual se compiló la imagen del paquete. En particular, si existe un conjunto diferente de métodos en el momento de carga en comparación con el momento de compilación de la imagen del paquete, el método debe ser invalidado y recompilado en el primer uso. Esto es necesario para garantizar que la semántica de ejecución permanezca igual, independientemente de si un paquete fue precompilado o si el código se ejecutó directamente. Las imágenes del sistema no necesitan realizar esta validación, ya que la tabla de métodos global está vacía en el momento de carga. Por lo tanto, las imágenes del sistema tienen tiempos de carga más rápidos que las imágenes de paquetes.
