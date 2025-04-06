# Environment Variables

Julia se puede configurar con una serie de variables de entorno, establecidas de la manera habitual para cada sistema operativo, o de una manera portátil desde dentro de Julia. Suponiendo que deseas establecer la variable de entorno [`JULIA_EDITOR`](@ref JULIA_EDITOR) a `vim`, puedes escribir `ENV["JULIA_EDITOR"] = "vim"` (por ejemplo, en el REPL) para hacer este cambio caso por caso, o agregar lo mismo al archivo de configuración del usuario `~/.julia/config/startup.jl` en el directorio personal del usuario para tener un efecto permanente. El valor actual de la misma variable de entorno se puede determinar evaluando `ENV["JULIA_EDITOR"]`.

Las variables de entorno que utiliza Julia generalmente comienzan con `JULIA`. Si [`InteractiveUtils.versioninfo`](@ref) se llama con la palabra clave `verbose=true`, entonces la salida enumerará cualquier variable de entorno definida relevante para Julia, incluyendo aquellas que incluyen `JULIA` en sus nombres.

!!! note
    Se recomienda evitar cambiar las variables de entorno durante el tiempo de ejecución, como dentro de un `~/.julia/config/startup.jl`.

    Una razón es que algunas variables del lenguaje julia, como [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) y [`JULIA_PROJECT`](@ref JULIA_PROJECT), deben configurarse antes de que Julia comience.

    De manera similar, las funciones `__init__()` de los módulos de usuario en la imagen del sistema (a través de PackageCompiler) se ejecutan antes de `startup.jl`, por lo que establecer variables de entorno en un `startup.jl` puede ser demasiado tarde para el código del usuario.

    Además, cambiar las variables de entorno durante la ejecución puede introducir condiciones de carrera en un código que de otro modo sería benigno.

    En Bash, las variables de entorno se pueden establecer manualmente ejecutando, por ejemplo, `export JULIA_NUM_THREADS=4` antes de iniciar Julia, o agregando el mismo comando a `~/.bashrc` o `~/.bash_profile` para establecer la variable cada vez que se inicia Bash.


## File locations

### [`JULIA_BINDIR`](@id JULIA_BINDIR)

La ruta absoluta del directorio que contiene el ejecutable de Julia, que establece la variable global [`Sys.BINDIR`](@ref). Si `$JULIA_BINDIR` no está configurado, entonces Julia determina el valor `Sys.BINDIR` en tiempo de ejecución.

El ejecutable en sí es uno de

```
$JULIA_BINDIR/julia
$JULIA_BINDIR/julia-debug
```

por defecto.

La variable global `Base.DATAROOTDIR` determina una ruta relativa desde `Sys.BINDIR` hasta el directorio de datos asociado con Julia. Luego, la ruta

```
$JULIA_BINDIR/$DATAROOTDIR/julia/base
```

determina el directorio en el que Julia busca inicialmente archivos fuente (a través de `Base.find_source_file()`).

Del mismo modo, la variable global `Base.SYSCONFDIR` determina una ruta relativa al directorio del archivo de configuración. Luego, Julia busca un archivo `startup.jl` en

```
$JULIA_BINDIR/$SYSCONFDIR/julia/startup.jl
$JULIA_BINDIR/../etc/julia/startup.jl
```

por defecto (a través de `Base.load_julia_startup()`).

Por ejemplo, una instalación de Linux con un ejecutable de Julia ubicado en `/bin/julia`, un `DATAROOTDIR` de `../share`, y un `SYSCONFDIR` de `../etc` tendrá [`JULIA_BINDIR`](@ref JULIA_BINDIR) configurado en `/bin`, una ruta de búsqueda de archivos fuente de

```
/share/julia/base
```

y una ruta de búsqueda de configuración global de

```
/etc/julia/startup.jl
```

### [`JULIA_PROJECT`](@id JULIA_PROJECT)

Un camino de directorio que indica qué proyecto debe ser el proyecto activo inicial. Establecer esta variable de entorno tiene el mismo efecto que especificar la opción de inicio `--project`, pero `--project` tiene mayor precedencia. Si la variable se establece en `@.` (nota el punto final), entonces Julia intenta encontrar un directorio de proyecto que contenga el archivo `Project.toml` o `JuliaProject.toml` desde el directorio actual y sus padres. Consulta también el capítulo sobre [Code Loading](@ref code-loading).

!!! note
    [`JULIA_PROJECT`](@ref JULIA_PROJECT) must be defined before starting julia; defining it in `startup.jl` is too late in the startup process.


### [`JULIA_LOAD_PATH`](@id JULIA_LOAD_PATH)

La variable de entorno [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) se utiliza para poblar la variable global de Julia [`LOAD_PATH`](@ref), que determina qué paquetes se pueden cargar a través de `import` y `using` (ver [Code Loading](@ref code-loading)).

A diferencia de la variable `PATH` del shell, las entradas vacías en [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) se expanden al valor predeterminado de `LOAD_PATH`, `["@", "@v#.#", "@stdlib"]` al poblar `LOAD_PATH`. Esto permite una fácil adición, prependido, etc. del valor de la ruta de carga en scripts de shell, independientemente de si `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` ya está configurado o no. Por ejemplo, para agregar el directorio `/foo/bar` al inicio de `LOAD_PATH`, simplemente haz

```sh
export JULIA_LOAD_PATH="/foo/bar:$JULIA_LOAD_PATH"
```

Si la variable de entorno [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) ya está establecida, su antiguo valor se antepondrá con `/foo/bar`. Por otro lado, si `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` no está establecida, entonces se establecerá en `/foo/bar:` lo que se expandirá a un valor de `LOAD_PATH` de `["/foo/bar", "@", "@v#.#", "@stdlib"]`. Si `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` está establecido como una cadena vacía, se expande a un array `LOAD_PATH` vacío. En otras palabras, la cadena vacía se interpreta como un array de cero elementos, no como un array de un elemento que es la cadena vacía. Este comportamiento fue elegido para que fuera posible establecer una ruta de carga vacía a través de la variable de entorno. Si deseas la ruta de carga predeterminada, ya sea desestableciendo la variable de entorno o, si debe tener un valor, estableciéndola en la cadena `:`.

!!! note
    En Windows, los elementos de la ruta están separados por el `;` carácter, como es el caso con la mayoría de las listas de rutas en Windows. Reemplace `:` con `;` en el párrafo anterior.


### [`JULIA_DEPOT_PATH`](@id JULIA_DEPOT_PATH)

La variable de entorno [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) se utiliza para poblar la variable global Julia [`DEPOT_PATH`](@ref), que controla dónde el administrador de paquetes, así como los mecanismos de carga de código de Julia, buscan registros de paquetes, paquetes instalados, entornos nombrados, clones de repositorios, imágenes de paquetes compilados en caché, archivos de configuración y la ubicación predeterminada del archivo de historial del REPL.

A diferencia de la variable `PATH` del shell, pero similar a [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH), las entradas vacías en [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) tienen un comportamiento especial:

  * Al final, se expande al valor predeterminado de `DEPOT_PATH`, *excluyendo* el depósito del usuario.
  * Al principio, se expande al valor predeterminado de `DEPOT_PATH`, *incluyendo* el depósito del usuario.

Esto permite una fácil anulación del depósito del usuario, mientras se mantiene el acceso a los recursos que están empaquetados con Julia, como archivos de caché, artefactos, etc. Por ejemplo, para cambiar el depósito del usuario a `/foo/bar`, usa un `:` al final.

```sh
export JULIA_DEPOT_PATH="/foo/bar:"
```

Todas las operaciones de paquetes, como clonar registros o instalar paquetes, ahora escribirán en `/foo/bar`, pero dado que la entrada vacía se expande al depósito del sistema por defecto, cualquier recurso empaquetado seguirá estando disponible. Si realmente solo deseas usar el depósito en `/foo/bar`, y no cargar ningún recurso empaquetado, simplemente establece la variable de entorno en `/foo/bar` sin el dos puntos al final.

Para agregar un depósito al final de la lista completa por defecto, incluyendo el depósito de usuario por defecto, usa un `:` al principio.

```sh
export JULIA_DEPOT_PATH=":/foo/bar"
```

Hay dos excepciones a la regla anterior. Primero, si [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) se establece como una cadena vacía, se expande a un array `DEPOT_PATH` vacío. En otras palabras, la cadena vacía se interpreta como un array de cero elementos, no como un array de un elemento que es la cadena vacía. Este comportamiento se eligió para que fuera posible establecer una ruta de depósito vacía a través de la variable de entorno.

En segundo lugar, si no se especifica un depósito de usuario en [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH), entonces la entrada vacía se expande al depósito predeterminado *incluyendo* el depósito de usuario. Esto hace posible usar el depósito predeterminado, como si la variable de entorno no estuviera establecida, al configurarla con la cadena `:`.

!!! note
    En Windows, los elementos de la ruta están separados por el `;` carácter, como es el caso con la mayoría de las listas de rutas en Windows. Reemplace `:` con `;` en el párrafo anterior.


!!! note
    [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) debe ser definido antes de iniciar julia; definirlo en `startup.jl` es demasiado tarde en el proceso de inicio; en ese momento, puedes en su lugar modificar directamente el array `DEPOT_PATH`, que se llena a partir de la variable de entorno.


### [`JULIA_HISTORY`](@id JULIA_HISTORY)

La ruta absoluta `REPL.find_hist_file()` del archivo de historial del REPL. Si `$JULIA_HISTORY` no está configurado, entonces `REPL.find_hist_file()` por defecto a

```
$(DEPOT_PATH[1])/logs/repl_history.jl
```

### [`JULIA_MAX_NUM_PRECOMPILE_FILES`](@id JULIA_MAX_NUM_PRECOMPILE_FILES)

Establece el número máximo de instancias diferentes de un solo paquete que se almacenarán en la caché de precompilación (predeterminado = 10).

### [`JULIA_VERBOSE_LINKING`](@id JULIA_VERBOSE_LINKING)

Si se establece en verdadero, se mostrarán los comandos del enlazador durante la precompilación.

## Pkg.jl

### [`JULIA_CI`](@id JULIA_CI)

Si se establece en `true`, esto indica al servidor de paquetes que cualquier operación de paquete es parte de un sistema de integración continua (CI) con el propósito de recopilar estadísticas de uso de paquetes.

### [`JULIA_NUM_PRECOMPILE_TASKS`](@id JULIA_NUM_PRECOMPILE_TASKS)

El número de tareas paralelas a utilizar al precompilar paquetes. Ver [`Pkg.precompile`](https://pkgdocs.julialang.org/v1/api/#Pkg.precompile).

### [`JULIA_PKG_DEVDIR`](@id JULIA_PKG_DEVDIR)

El directorio predeterminado utilizado por [`Pkg.develop`](https://pkgdocs.julialang.org/v1/api/#Pkg.develop) para descargar paquetes.

### [`JULIA_PKG_IGNORE_HASHES`](@id JULIA_PKG_IGNORE_HASHES)

Si se establece en `1`, esto ignorará los hashes incorrectos en los artefactos. Esto debe usarse con cuidado, ya que desactiva la verificación de descargas, pero puede resolver problemas al mover archivos entre diferentes tipos de sistemas de archivos. Consulte [Pkg.jl issue #2317](https://github.com/JuliaLang/Pkg.jl/issues/2317) para más detalles.

!!! compat "Julia 1.6"
    Esto solo es compatible con Julia 1.6 y versiones superiores.


### [`JULIA_PKG_OFFLINE`](@id JULIA_PKG_OFFLINE)

Si se establece en `true`, esto habilitará el modo fuera de línea: ver [`Pkg.offline`](https://pkgdocs.julialang.org/v1/api/#Pkg.offline).

!!! compat "Julia 1.5"
    El modo offline de Pkg requiere Julia 1.5 o posterior.


### [`JULIA_PKG_PRECOMPILE_AUTO`](@id JULIA_PKG_PRECOMPILE_AUTO)

Si se establece en `0`, esto desactivará la precompilación automática por acciones de paquete que cambian el manifiesto. Ver [`Pkg.precompile`](https://pkgdocs.julialang.org/v1/api/#Pkg.precompile).

### [`JULIA_PKG_SERVER`](@id JULIA_PKG_SERVER)

Especifica la URL del registro de paquetes a utilizar. Por defecto, `Pkg` utiliza `https://pkg.julialang.org` para obtener paquetes de Julia. Además, puedes deshabilitar el uso del protocolo PkgServer y, en su lugar, acceder a los paquetes directamente desde sus anfitriones (GitHub, GitLab, etc.) configurando: `export JULIA_PKG_SERVER=""`

### [`JULIA_PKG_SERVER_REGISTRY_PREFERENCE`](@id JULIA_PKG_SERVER_REGISTRY_PREFERENCE)

Especifica el sabor de registro preferido. Los valores actualmente soportados son `conservative` (el predeterminado), que solo publicará recursos que han sido procesados por el servidor de almacenamiento (y que, por lo tanto, tienen una mayor probabilidad de estar disponibles desde los PkgServers), mientras que `eager` publicará registros cuyos recursos no necesariamente han sido procesados por los servidores de almacenamiento. Los usuarios detrás de firewalls restrictivos que no permiten la descarga desde servidores arbitrarios no deben usar el sabor `eager`.

!!! compat "Julia 1.7"
    Esto solo afecta a Julia 1.7 y versiones superiores.


### [`JULIA_PKG_UNPACK_REGISTRY`](@id JULIA_PKG_UNPACK_REGISTRY)

Si se establece en `true`, esto descomprimirá el registro en lugar de almacenarlo como un tarball comprimido.

!!! compat "Julia 1.7"
    Esto solo afecta a Julia 1.7 y versiones superiores. Las versiones anteriores siempre descomprimirán el registro.


### [`JULIA_PKG_USE_CLI_GIT`](@id JULIA_PKG_USE_CLI_GIT)

Si se establece en `true`, las operaciones de Pkg que utilizan el protocolo git usarán un ejecutable `git` externo en lugar de la biblioteca libgit2 predeterminada.

!!! compat "Julia 1.7"
    El uso del ejecutable `git` solo es compatible con Julia 1.7 y versiones superiores.


### [`JULIA_PKGRESOLVE_ACCURACY`](@id JULIA_PKGRESOLVE_ACCURACY)

La precisión del resolutor de paquetes. Este debe ser un número entero positivo, el valor predeterminado es `1`.

### [`JULIA_PKG_PRESERVE_TIERED_INSTALLED`](@id JULIA_PKG_PRESERVE_TIERED_INSTALLED)

Cambia la estrategia de instalación de paquetes predeterminada a `Pkg.PRESERVE_TIERED_INSTALLED` para permitir que el administrador de paquetes intente instalar versiones de paquetes mientras mantiene tantas versiones de paquetes ya instaladas como sea posible.

!!! compat "Julia 1.9"
    Esto solo afecta a Julia 1.9 y versiones superiores.


## Network transport

### [`JULIA_NO_VERIFY_HOSTS`](@id JULIA_NO_VERIFY_HOSTS)

### [`JULIA_SSL_NO_VERIFY_HOSTS`](@id JULIA_SSL_NO_VERIFY_HOSTS)

### [`JULIA_SSH_NO_VERIFY_HOSTS`](@id JULIA_SSH_NO_VERIFY_HOSTS)

### [`JULIA_ALWAYS_VERIFY_HOSTS`](@id JULIA_ALWAYS_VERIFY_HOSTS)

Especificar hosts cuya identidad debe o no debe ser verificada para capas de transporte específicas. Ver [`NetworkOptions.verify_host`](https://github.com/JuliaLang/NetworkOptions.jl#verify_host)

### [`JULIA_SSL_CA_ROOTS_PATH`](@id JULIA_SSL_CA_ROOTS_PATH)

Especifica el archivo o directorio que contiene las raíces de la autoridad de certificación. Ver [`NetworkOptions.ca_roots`](https://github.com/JuliaLang/NetworkOptions.jl#ca_roots)

## External applications

### [`JULIA_SHELL`](@id JULIA_SHELL)

La ruta absoluta del shell con el que Julia debe ejecutar comandos externos (a través de `Base.repl_cmd()`). Por defecto, se establece en la variable de entorno `$SHELL`, y se utiliza `/bin/sh` si `$SHELL` no está configurada.

!!! note
    En Windows, esta variable de entorno es ignorada, y los comandos externos se ejecutan directamente.


### [`JULIA_EDITOR`](@id JULIA_EDITOR)

El editor devuelto por `InteractiveUtils.editor()` y utilizado en, por ejemplo, [`InteractiveUtils.edit`](@ref), se refiere al comando del editor preferido, por ejemplo `vim`.

`$JULIA_EDITOR` tiene prioridad sobre `$VISUAL`, que a su vez tiene prioridad sobre `$EDITOR`. Si ninguna de estas variables de entorno está configurada, entonces el editor se considera `open` en Windows y OS X, o `/etc/alternatives/editor` si existe, o `emacs` de lo contrario.

Para usar Visual Studio Code en Windows, establece `$JULIA_EDITOR` en `code.cmd`.

## Parallelization

### [`JULIA_CPU_THREADS`](@id JULIA_CPU_THREADS)

Sobrescribe la variable global [`Base.Sys.CPU_THREADS`](@ref), el número de núcleos de CPU lógicos disponibles.

### [`JULIA_WORKER_TIMEOUT`](@id JULIA_WORKER_TIMEOUT)

Un [`Float64`](@ref) que establece el valor de `Distributed.worker_timeout()` (por defecto: `60.0`). Esta función da el número de segundos que un proceso trabajador esperará a que un proceso maestro establezca una conexión antes de morir.

### [`JULIA_NUM_THREADS`](@id JULIA_NUM_THREADS)

Un entero sin signo de 64 bits (`uint64_t`) que establece el número máximo de hilos disponibles para Julia. Si `$JULIA_NUM_THREADS` no es positivo o no está configurado, o si el número de hilos de CPU no se puede determinar a través de llamadas al sistema, entonces el número de hilos se establece en `1`.

Si `$JULIA_NUM_THREADS` está configurado en `auto`, entonces el número de hilos se establecerá en el número de hilos de CPU.

!!! note
    `JULIA_NUM_THREADS` debe definirse antes de iniciar julia; definirlo en `startup.jl` es demasiado tarde en el proceso de inicio.


!!! compat "Julia 1.5"
    En Julia 1.5 y versiones posteriores, el número de hilos también se puede especificar al inicio utilizando el argumento de línea de comandos `-t`/`--threads`.


!!! compat "Julia 1.7"
    El valor `auto` para `$JULIA_NUM_THREADS` requiere Julia 1.7 o superior.


### [`JULIA_THREAD_SLEEP_THRESHOLD`](@id JULIA_THREAD_SLEEP_THRESHOLD)

Si se establece en una cadena que comienza con la subcadena insensible a mayúsculas `"infinite"`, entonces los hilos en espera nunca duermen. De lo contrario, `$JULIA_THREAD_SLEEP_THRESHOLD` se interpreta como un entero sin signo de 64 bits (`uint64_t`) y da, en nanosegundos, la cantidad de tiempo después de la cual los hilos en espera deberían dormir.

### [`JULIA_NUM_GC_THREADS`](@id JULIA_NUM_GC_THREADS)

Establece el número de hilos utilizados por la recolección de basura. Si no se especifica, se establece en la mitad del número de hilos de trabajo.

!!! compat "Julia 1.10"
    La variable de entorno se agregó en 1.10


### [`JULIA_IMAGE_THREADS`](@id JULIA_IMAGE_THREADS)

Un entero sin signo de 32 bits que establece el número de hilos utilizados por la compilación de imágenes en este proceso de Julia. El valor de esta variable puede ser ignorado si el módulo es un módulo pequeño. Si se deja sin especificar, se utiliza el menor de los valores de [`JULIA_CPU_THREADS`](@ref JULIA_CPU_THREADS) o la mitad del número de núcleos lógicos de la CPU en su lugar.

### [`JULIA_IMAGE_TIMINGS`](@id JULIA_IMAGE_TIMINGS)

Un valor booleano que determina si se imprime información de tiempo detallada durante la compilación de la imagen. Por defecto es 0.

### [`JULIA_EXCLUSIVE`](@id JULIA_EXCLUSIVE)

Si se establece en cualquier valor diferente de `0`, entonces la política de hilos de Julia es consistente con la ejecución en una máquina dedicada: el hilo maestro está en el proc 0 y los hilos están afinizados. De lo contrario, Julia permite que el sistema operativo maneje la política de hilos.

## REPL formatting

Variables de entorno que determinan cómo se debe formatear la salida de REPL en el terminal. Generalmente, estas variables deben establecerse en [ANSI terminal escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code). Julia proporciona una interfaz de alto nivel con gran parte de la misma funcionalidad; consulte la sección sobre [The Julia REPL](@ref).

### [`JULIA_ERROR_COLOR`](@id JULIA_ERROR_COLOR)

El formato `Base.error_color()` (predeterminado: rojo claro, `"\033[91m"`) que los errores deben tener en la terminal.

### [`JULIA_WARN_COLOR`](@id JULIA_WARN_COLOR)

El formato `Base.warn_color()` (predeterminado: amarillo, `"\033[93m"`) que deben tener las advertencias en la terminal.

### [`JULIA_INFO_COLOR`](@id JULIA_INFO_COLOR)

El formato `Base.info_color()` (predeterminado: cian, `"\033[36m"`) que la información debería tener en la terminal.

### [`JULIA_INPUT_COLOR`](@id JULIA_INPUT_COLOR)

El formato `Base.input_color()` (predeterminado: normal, `"\033[0m"`) que la entrada debe tener en la terminal.

### [`JULIA_ANSWER_COLOR`](@id JULIA_ANSWER_COLOR)

El formato `Base.answer_color()` (predeterminado: normal, `"\033[0m"`) que la salida debería tener en la terminal.

## System and Package Image Building

### [`JULIA_CPU_TARGET`](@id JULIA_CPU_TARGET)

Modifique la arquitectura de la máquina objetivo para (pre)compilar [system](@ref sysimg-multi-versioning) y [package images](@ref pkgimgs-multi-versioning). `JULIA_CPU_TARGET` solo afecta la generación de imágenes de código de máquina que se envían a un caché en disco. A diferencia de `--cpu-target`, o `-C`, [command line option](@ref cli), no influye en la generación de código en tiempo de ejecución (JIT) dentro de una sesión de Julia donde el código de máquina solo se almacena en memoria.

Los valores válidos para [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) se pueden obtener ejecutando `julia -C help`.

Configurar [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) es importante para sistemas de computación heterogénea donde pueden estar presentes procesadores de distintos tipos o características. Esto se encuentra comúnmente en clústeres de computación de alto rendimiento (HPC) ya que los nodos de componentes pueden estar utilizando procesadores distintos.

La cadena de destino de la CPU es una lista de cadenas separadas por `;` cada cadena comienza con un nombre de CPU o arquitectura y es seguida por una lista opcional de características separadas por `,`. Un nombre de CPU `genérico` o vacío significa el conjunto básico de características requeridas del ISA de destino, que es al menos la arquitectura con la que se compila el tiempo de ejecución de C/C++. Cada cadena es interpretada por LLVM.

Se admiten algunas características especiales:

1. `clonar_todo`

    Esto obliga al objetivo a tener todas las funciones en sysimg clonadas. Cuando se usa en forma negativa (es decir, `-clone_all`), esto desactiva la clonación completa que está habilitada por defecto para ciertos objetivos.
2. `base([0-9]*)`

    Esto especifica el índice de objetivo base (basado en 0). El objetivo base es el objetivo en el que se basa el objetivo actual, es decir, las funciones que no se están clonando utilizarán la versión en el objetivo base. Esta opción provoca que el objetivo base se clone completamente (como si se especificara `clone_all` para él) si no es el objetivo predeterminado (0). El índice solo puede ser menor que el índice actual.
3. `opt_size`

    Optimizar para tamaño con un impacto mínimo en el rendimiento. `-Os` de Clang/GCC.
4. `min_size`

    Optimizar solo para tamaño. `-Oz` de Clang.

## Debugging and profiling

### [`JULIA_DEBUG`](@id JULIA_DEBUG)

Habilite el registro de depuración para un archivo o módulo, consulte [`Logging`](@ref man-logging) para más información.

### [`JULIA_PROFILE_PEEK_HEAP_SNAPSHOT`](@id JULIA_PROFILE_PEEK_HEAP_SNAPSHOT)

Habilitar la recopilación de un instantáneo de heap durante la ejecución a través del mecanismo de vista de perfil. Ver [Triggered During Execution](@ref).

### [`JULIA_TIMING_SUBSYSTEMS`](@id JULIA_TIMING_SUBSYSTEMS)

Permite habilitar o deshabilitar zonas para una ejecución específica de Julia. Por ejemplo, establecer la variable en `+GC,-INFERENCE` habilitará las zonas de `GC` y deshabilitará las zonas de `INFERENCE`. Consulta [Dynamically Enabling and Disabling Zones](@ref).

### [`JULIA_GC_ALLOC_POOL`](@id JULIA_GC_ALLOC_POOL)

### [`JULIA_GC_ALLOC_OTHER`](@id JULIA_GC_ALLOC_OTHER)

### [`JULIA_GC_ALLOC_PRINT`](@id JULIA_GC_ALLOC_PRINT)

Si se establecen, estas variables de entorno toman cadenas que opcionalmente comienzan con el carácter `'r'`, seguidas de una interpolación de cadena de una lista separada por dos puntos de tres enteros con signo de 64 bits (`int64_t`). Este trío de enteros `a:b:c` representa la secuencia aritmética `a`, `a + b`, `a + 2*b`, ... `c`.

  * Si es la `n`-ésima vez que se ha llamado a `jl_gc_pool_alloc()`, y `n` pertenece a la secuencia aritmética representada por `$JULIA_GC_ALLOC_POOL`, entonces se fuerza la recolección de basura.
  * Si es la `n`-ésima vez que se ha llamado a `maybe_collect()`, y `n` pertenece a la secuencia aritmética representada por `$JULIA_GC_ALLOC_OTHER`, entonces se fuerza la recolección de basura.
  * Si es la `n`-ésima vez que se ha llamado a `jl_gc_collect()`, y `n` pertenece a la secuencia aritmética representada por `$JULIA_GC_ALLOC_PRINT`, entonces se imprimen los conteos de las llamadas a `jl_gc_pool_alloc()` y `maybe_collect()`.

Si el valor de la variable de entorno comienza con el carácter `'r'`, entonces el intervalo entre los eventos de recolección de basura se aleatoriza.

!!! note
    Estas variables de entorno solo tienen efecto si Julia fue compilado con depuración de recolección de basura (es decir, si `WITH_GC_DEBUG_ENV` está configurado en `1` en la configuración de compilación).


### [`JULIA_GC_NO_GENERATIONAL`](@id JULIA_GC_NO_GENERATIONAL)

Si se establece en cualquier valor que no sea `0`, entonces el recolector de basura de Julia nunca realiza "barridos rápidos" de memoria.

!!! note
    Esta variable de entorno solo tiene efecto si Julia fue compilado con depuración de recolección de basura (es decir, si `WITH_GC_DEBUG_ENV` está configurado en `1` en la configuración de compilación).


### [`JULIA_GC_WAIT_FOR_DEBUGGER`](@id JULIA_GC_WAIT_FOR_DEBUGGER)

Si se establece en cualquier valor que no sea `0`, entonces el recolector de basura de Julia esperará a que un depurador se adjunte en lugar de abortar cada vez que haya un error crítico.

!!! note
    Esta variable de entorno solo tiene efecto si Julia fue compilado con depuración de recolección de basura (es decir, si `WITH_GC_DEBUG_ENV` está configurado en `1` en la configuración de compilación).


### [`ENABLE_JITPROFILING`](@id ENABLE_JITPROFILING)

Si se establece en cualquier valor que no sea `0`, entonces el compilador creará y registrará un oyente de eventos para el perfilado justo a tiempo (JIT).

!!! note
    Esta variable de entorno solo tiene efecto si Julia fue compilada con soporte de perfilado JIT, utilizando ya sea

      * Intel's [VTune™ Amplifier](https://software.intel.com/en-us/vtune) (`USE_INTEL_JITEVENTS` establecido en `1` en la configuración de compilación), o
      * [OProfile](https://oprofile.sourceforge.io/news/) (`USE_OPROFILE_JITEVENTS` configurado en `1` en la configuración de compilación).
      * [Perf](https://perf.wiki.kernel.org) (`USE_PERF_JITEVENTS` configurado en `1` en la configuración de compilación). Esta integración está habilitada por defecto.


### [`ENABLE_GDBLISTENER`](@id ENABLE_GDBLISTENER)

Si se establece en cualquier valor que no sea `0`, habilita el registro de GDB del código de Julia en compilaciones de lanzamiento. En las compilaciones de depuración de Julia, esto siempre está habilitado. Se recomienda usar con `-g 2`.

### [`JULIA_LLVM_ARGS`](@id JULIA_LLVM_ARGS)

Argumentos que se pasarán al backend de LLVM.

### `JULIA_FALLBACK_REPL`

Fuerza el repl de respaldo en lugar de REPL.jl.
