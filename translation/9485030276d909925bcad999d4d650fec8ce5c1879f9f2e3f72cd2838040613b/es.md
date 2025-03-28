# Embedding Julia

Como hemos visto en [Calling C and Fortran Code](@ref), Julia tiene una forma simple y eficiente de llamar funciones escritas en C. Pero hay situaciones en las que se necesita lo contrario: llamar funciones de Julia desde código C. Esto se puede usar para integrar código de Julia en un proyecto más grande de C/C++, sin necesidad de reescribir todo en C/C++. Julia tiene una API de C para hacer esto posible. Dado que casi todos los lenguajes de programación tienen alguna forma de llamar funciones de C, la API de C de Julia también se puede usar para construir puentes entre lenguajes adicionales (por ejemplo, llamar a Julia desde Python, Rust o C#). A pesar de que Rust y C++ pueden usar la API de incrustación de C directamente, ambos tienen paquetes que ayudan con ello; para C++ [Jluna](https://github.com/Clemapfel/jluna) es útil.

## High-Level Embedding

**Nota**: Esta sección cubre la incrustación de código Julia en C en sistemas operativos similares a Unix. Para hacerlo en Windows, consulte la sección siguiente, [High-Level Embedding on Windows with Visual Studio](@ref).

Comenzamos con un programa C simple que inicializa Julia y llama a algún código de Julia:

```c
#include <julia.h>
JULIA_DEFINE_FAST_TLS // only define this once, in an executable (not in a shared library) if you want fast code.

int main(int argc, char *argv[])
{
    /* required: setup the Julia context */
    jl_init();

    /* run Julia commands */
    jl_eval_string("print(sqrt(2.0))");

    /* strongly recommended: notify Julia that the
         program is about to terminate. this allows
         Julia time to cleanup pending write requests
         and run all finalizers
    */
    jl_atexit_hook(0);
    return 0;
}
```

Para construir este programa, debes agregar la ruta al encabezado de Julia a la ruta de inclusión y vincular contra `libjulia`. Por ejemplo, cuando Julia está instalada en `$JULIA_DIR`, se puede compilar el programa de prueba anterior `test.c` con `gcc` usando:

```
gcc -o test -fPIC -I$JULIA_DIR/include/julia -L$JULIA_DIR/lib -Wl,-rpath,$JULIA_DIR/lib test.c -ljulia
```

Alternativamente, mira el programa `embedding.c` en el árbol de fuentes de Julia en la carpeta `test/embedding/`. El archivo `cli/loader_exe.c` es otro ejemplo simple de cómo establecer las opciones `jl_options` mientras se vincula contra `libjulia`.

Lo primero que debe hacerse antes de llamar a cualquier otra función C de Julia es inicializar Julia. Esto se hace llamando a `jl_init`, que intenta determinar automáticamente la ubicación de instalación de Julia. Si necesitas especificar una ubicación personalizada o indicar qué imagen del sistema cargar, utiliza `jl_init_with_image` en su lugar.

La segunda declaración en el programa de prueba evalúa una declaración de Julia utilizando una llamada a `jl_eval_string`.

Antes de que el programa termine, se recomienda encarecidamente que se llame a `jl_atexit_hook`. El programa de ejemplo anterior llama a esto justo antes de regresar de `main`.

!!! note
    Actualmente, vincular dinámicamente con la biblioteca compartida `libjulia` requiere pasar la opción `RTLD_GLOBAL`. En Python, esto se ve así:

    ```
    >>> julia=CDLL('./libjulia.dylib',RTLD_GLOBAL)
    >>> julia.jl_init.argtypes = []
    >>> julia.jl_init()
    250593296
    ```


!!! note
    Si el programa de Julia necesita acceder a símbolos del ejecutable principal, puede ser necesario agregar la bandera del enlazador `-Wl,--export-dynamic` en el tiempo de compilación en Linux, además de las que genera `julia-config.jl` descritas a continuación. Esto no es necesario al compilar una biblioteca compartida.


### Using julia-config to automatically determine build parameters

El script `julia-config.jl` fue creado para ayudar a determinar qué parámetros de construcción son requeridos por un programa que utiliza Julia embebido. Este script utiliza los parámetros de construcción y la configuración del sistema de la distribución de Julia particular que se invoca para exportar las banderas de compilador necesarias para que un programa embebido interactúe con esa distribución. Este script se encuentra en el directorio de datos compartidos de Julia.

#### Example

```c
#include <julia.h>

int main(int argc, char *argv[])
{
    jl_init();
    (void)jl_eval_string("println(sqrt(2.0))");
    jl_atexit_hook(0);
    return 0;
}
```

#### On the command line

Un uso simple de este script es desde la línea de comandos. Suponiendo que `julia-config.jl` se encuentra en `/usr/local/julia/share/julia`, se puede invocar directamente en la línea de comandos y acepta cualquier combinación de tres flags:

```
/usr/local/julia/share/julia/julia-config.jl
Usage: julia-config [--cflags|--ldflags|--ldlibs]
```

Si el ejemplo de código anterior se guarda en el archivo `embed_example.c`, entonces el siguiente comando lo compilará en un programa ejecutable en Linux y Windows (entorno MSYS2). En macOS, sustituya `gcc` por `clang`.

```
/usr/local/julia/share/julia/julia-config.jl --cflags --ldflags --ldlibs | xargs gcc embed_example.c
```

#### Use in Makefiles

En general, los proyectos de incrustación serán más complicados que el ejemplo anterior, por lo que lo siguiente también permite soporte general para makefile, asumiendo GNU make debido al uso de las expansiones de macros **shell**. Además, aunque `julia-config.jl` suele estar en el directorio `/usr/local`, si no lo está, entonces Julia misma puede ser utilizada para encontrar `julia-config.jl`, y el makefile puede aprovechar esto. El ejemplo anterior se extiende para usar un makefile:

```
JL_SHARE = $(shell julia -e 'print(joinpath(Sys.BINDIR, Base.DATAROOTDIR, "julia"))')
CFLAGS   += $(shell $(JL_SHARE)/julia-config.jl --cflags)
CXXFLAGS += $(shell $(JL_SHARE)/julia-config.jl --cflags)
LDFLAGS  += $(shell $(JL_SHARE)/julia-config.jl --ldflags)
LDLIBS   += $(shell $(JL_SHARE)/julia-config.jl --ldlibs)

all: embed_example
```

Ahora el comando de construcción es simplemente `make`.

## High-Level Embedding on Windows with Visual Studio

Si la variable de entorno `JULIA_DIR` no ha sido configurada, agrégala utilizando el panel del Sistema antes de iniciar Visual Studio. La carpeta `bin` bajo JULIA_DIR debería estar en la ruta del sistema.

Comenzamos abriendo Visual Studio y creando un nuevo proyecto de Aplicación de Consola. Abre el archivo de encabezado 'stdafx.h' y agrega las siguientes líneas al final:

```c
#include <julia.h>
```

Luego, reemplaza la función main() en el proyecto con este código:

```c
int main(int argc, char *argv[])
{
    /* required: setup the Julia context */
    jl_init();

    /* run Julia commands */
    jl_eval_string("print(sqrt(2.0))");

    /* strongly recommended: notify Julia that the
         program is about to terminate. this allows
         Julia time to cleanup pending write requests
         and run all finalizers
    */
    jl_atexit_hook(0);
    return 0;
}
```

El siguiente paso es configurar el proyecto para encontrar los archivos de inclusión de Julia y las bibliotecas. Es importante saber si la instalación de Julia es de 32 o 64 bits. Elimina cualquier configuración de plataforma que no corresponda a la instalación de Julia antes de continuar.

Usando el diálogo de propiedades del proyecto, ve a `C/C++` | `General` y agrega `$(JULIA_DIR)\include\julia\` a la propiedad Directorios de Inclusión Adicionales. Luego, ve a la sección `Linker` | `General` y agrega `$(JULIA_DIR)\lib` a la propiedad Directorios de Bibliotecas Adicionales. Finalmente, bajo `Linker` | `Input`, agrega `libjulia.dll.a;libopenlibm.dll.a;` a la lista de bibliotecas.

En este punto, el proyecto debería compilar y ejecutarse.

## Converting Types

Las aplicaciones reales no solo necesitarán ejecutar expresiones, sino también devolver sus valores al programa anfitrión. `jl_eval_string` devuelve un `jl_value_t*`, que es un puntero a un objeto de Julia asignado en el heap. Almacenar tipos de datos simples como [`Float64`](@ref) de esta manera se llama `boxing`, y extraer los datos primitivos almacenados se llama `unboxing`. Nuestro programa de muestra mejorado que calcula la raíz cuadrada de 2 en Julia y lee el resultado en C tiene un cuerpo que ahora contiene este código:

```c
jl_value_t *ret = jl_eval_string("sqrt(2.0)");

if (jl_typeis(ret, jl_float64_type)) {
    double ret_unboxed = jl_unbox_float64(ret);
    printf("sqrt(2.0) in C: %e \n", ret_unboxed);
}
else {
    printf("ERROR: unexpected return type from sqrt(::Float64)\n");
}
```

Para verificar si `ret` es de un tipo específico de Julia, podemos usar las funciones `jl_isa`, `jl_typeis` o `jl_is_...`. Al escribir `typeof(sqrt(2.0))` en la consola de Julia, podemos ver que el tipo de retorno es [`Float64`](@ref) (`double` en C). Para convertir el valor de Julia en caja a un double de C, se utiliza la función `jl_unbox_float64` en el fragmento de código anterior.

Las funciones correspondientes `jl_box_...` se utilizan para convertir en la otra dirección:

```c
jl_value_t *a = jl_box_float64(3.0);
jl_value_t *b = jl_box_float32(3.0f);
jl_value_t *c = jl_box_int32(3);
```

Como veremos a continuación, el boxing es necesario para llamar a funciones de Julia con argumentos específicos.

## Calling Julia Functions

Mientras que `jl_eval_string` permite que C obtenga el resultado de una expresión de Julia, no permite pasar argumentos calculados en C a Julia. Para esto, necesitarás invocar funciones de Julia directamente, utilizando `jl_call`:

```c
jl_function_t *func = jl_get_function(jl_base_module, "sqrt");
jl_value_t *argument = jl_box_float64(2.0);
jl_value_t *ret = jl_call1(func, argument);
```

En el primer paso, se obtiene un manejador de la función de Julia `sqrt` llamando a `jl_get_function`. El primer argumento pasado a `jl_get_function` es un puntero al módulo `Base` en el que se define `sqrt`. Luego, el valor de punto flotante se encapsula utilizando `jl_box_float64`. Finalmente, en el último paso, la función se llama usando `jl_call1`. También existen las funciones `jl_call0`, `jl_call2` y `jl_call3`, para manejar convenientemente diferentes números de argumentos. Para pasar más argumentos, utiliza `jl_call`:

```
jl_value_t *jl_call(jl_function_t *f, jl_value_t **args, int32_t nargs)
```

Su segundo argumento `args` es un array de `jl_value_t*` argumentos y `nargs` es el número de argumentos.

También hay una alternativa, posiblemente más simple, para llamar a funciones de Julia y es a través de [`@cfunction`](@ref). Usar `@cfunction` te permite hacer las conversiones de tipo en el lado de Julia, lo cual es típicamente más fácil que hacerlo en el lado de C. El ejemplo de `sqrt` anterior se escribiría con `@cfunction` como:

```c
double (*sqrt_jl)(double) = jl_unbox_voidpointer(jl_eval_string("@cfunction(sqrt, Float64, (Float64,))"));
double ret = sqrt_jl(2.0);
```

donde primero definimos una función llamable desde C en Julia, extraemos el puntero de la función de ella y finalmente la llamamos. Además de simplificar las conversiones de tipo al realizarlas en el lenguaje de nivel superior, llamar a funciones de Julia a través de punteros `@cfunction` elimina la sobrecarga de despacho dinámico requerida por `jl_call` (para la cual todos los argumentos están "encapsulados"), y debería tener un rendimiento equivalente al de los punteros de función nativos de C.

## Memory Management

Como hemos visto, los objetos de Julia se representan en C como punteros del tipo `jl_value_t*`. Esto plantea la pregunta de quién es responsable de liberar estos objetos.

Típicamente, los objetos de Julia son liberados por el recolector de basura (GC), pero el GC no sabe automáticamente que estamos manteniendo una referencia a un valor de Julia desde C. Esto significa que el GC puede liberar objetos sin que lo sepamos, invalidando los punteros.

El GC solo se ejecutará cuando se estén asignando nuevos objetos de Julia. Llamadas como `jl_box_float64` realizan asignaciones, pero la asignación también puede ocurrir en cualquier momento durante la ejecución del código de Julia.

Al escribir código que incrusta Julia, generalmente es seguro usar valores `jl_value_t*` entre llamadas `jl_...` (ya que el GC solo se activará con esas llamadas). Pero para asegurarnos de que los valores puedan sobrevivir a las llamadas `jl_...`, tenemos que decirle a Julia que aún mantenemos una referencia a los valores Julia [root](https://www.cs.purdue.edu/homes/hosking/690M/p611-fenichel.pdf), un proceso llamado "enraizamiento del GC". Enraizar un valor asegurará que el recolector de basura no identifique accidentalmente este valor como no utilizado y libere la memoria que respalda ese valor. Esto se puede hacer utilizando las macros `JL_GC_PUSH`:

```c
jl_value_t *ret = jl_eval_string("sqrt(2.0)");
JL_GC_PUSH1(&ret);
// Do something with ret
JL_GC_POP();
```

La llamada `JL_GC_POP` libera las referencias establecidas por el anterior `JL_GC_PUSH`. Tenga en cuenta que `JL_GC_PUSH` almacena referencias en la pila de C, por lo que debe estar emparejado exactamente con un `JL_GC_POP` antes de que se salga del ámbito. Es decir, antes de que la función regrese, o el flujo de control salga de otro modo del bloque en el que se invocó `JL_GC_PUSH`.

Varios valores de Julia se pueden agregar a la vez utilizando los macros `JL_GC_PUSH2` a `JL_GC_PUSH6`:

```
JL_GC_PUSH2(&ret1, &ret2);
// ...
JL_GC_PUSH6(&ret1, &ret2, &ret3, &ret4, &ret5, &ret6);
```

Para empujar un array de valores de Julia se puede usar el macro `JL_GC_PUSHARGS`, que se puede utilizar de la siguiente manera:

```c
jl_value_t **args;
JL_GC_PUSHARGS(args, 2); // args can now hold 2 `jl_value_t*` objects
args[0] = some_value;
args[1] = some_other_value;
// Do something with args (e.g. call jl_... functions)
JL_GC_POP();
```

Cada ámbito debe tener solo una llamada a `JL_GC_PUSH*`, y debe estar emparejada con una única llamada a `JL_GC_POP`. Si todas las variables necesarias que deseas anclar no pueden ser empujadas con una sola llamada a `JL_GC_PUSH*`, o si hay más de 6 variables que deben ser empujadas y usar un arreglo de argumentos no es una opción, entonces se pueden usar bloques internos:

```c
jl_value_t *ret1 = jl_eval_string("sqrt(2.0)");
JL_GC_PUSH1(&ret1);
jl_value_t *ret2 = 0;
{
    jl_function_t *func = jl_get_function(jl_base_module, "exp");
    ret2 = jl_call1(func, ret1);
    JL_GC_PUSH1(&ret2);
    // Do something with ret2.
    JL_GC_POP();    // This pops ret2.
}
JL_GC_POP();    // This pops ret1.
```

Tenga en cuenta que no es necesario tener valores válidos de `jl_value_t*` antes de llamar a `JL_GC_PUSH*`. Está bien tener varios de ellos inicializados a `NULL`, pasarlos a `JL_GC_PUSH*` y luego crear los valores de Julia reales. Por ejemplo:

```
jl_value_t *ret1 = NULL, *ret2 = NULL;
JL_GC_PUSH2(&ret1, &ret2);
ret1 = jl_eval_string("sqrt(2.0)");
ret2 = jl_eval_string("sqrt(3.0)");
// Use ret1 and ret2
JL_GC_POP();
```

Si se requiere mantener el puntero a una variable entre funciones (o ámbitos de bloque), entonces no es posible usar `JL_GC_PUSH*`. En este caso, es necesario crear y mantener una referencia a la variable en el ámbito global de Julia. Una forma sencilla de lograr esto es usar un `IdDict` global que mantenga las referencias, evitando la desasignación por parte del GC. Sin embargo, este método solo funcionará correctamente con tipos mutables.

```c
// This functions shall be executed only once, during the initialization.
jl_value_t* refs = jl_eval_string("refs = IdDict()");
jl_function_t* setindex = jl_get_function(jl_base_module, "setindex!");

...

// `var` is the variable we want to protect between function calls.
jl_value_t* var = 0;

...

// `var` is a `Vector{Float64}`, which is mutable.
var = jl_eval_string("[sqrt(2.0); sqrt(4.0); sqrt(6.0)]");

// To protect `var`, add its reference to `refs`.
jl_call3(setindex, refs, var, var);
```

Si la variable es inmutable, entonces debe estar envuelta en un contenedor mutable equivalente o, preferiblemente, en un `RefValue{Any}` antes de ser añadida a `IdDict`. En este enfoque, el contenedor debe ser creado o llenado a través de código C utilizando, por ejemplo, la función `jl_new_struct`. Si el contenedor es creado por `jl_call*`, entonces necesitarás recargar el puntero para ser utilizado en el código C.

```c
// This functions shall be executed only once, during the initialization.
jl_value_t* refs = jl_eval_string("refs = IdDict()");
jl_function_t* setindex = jl_get_function(jl_base_module, "setindex!");
jl_datatype_t* reft = (jl_datatype_t*)jl_eval_string("Base.RefValue{Any}");

...

// `var` is the variable we want to protect between function calls.
jl_value_t* var = 0;

...

// `var` is a `Float64`, which is immutable.
var = jl_eval_string("sqrt(2.0)");

// Protect `var` until we add its reference to `refs`.
JL_GC_PUSH1(&var);

// Wrap `var` in `RefValue{Any}` and push to `refs` to protect it.
jl_value_t* rvar = jl_new_struct(reft, var);
JL_GC_POP();

jl_call3(setindex, refs, rvar, rvar);
```

El GC puede permitir la desasignación de una variable eliminando la referencia a ella de `refs` utilizando la función `delete!`, siempre que no se mantenga ninguna otra referencia a la variable en ningún lugar:

```c
jl_function_t* delete = jl_get_function(jl_base_module, "delete!");
jl_call2(delete, refs, rvar);
```

Como alternativa para casos muy simples, es posible crear un contenedor global de tipo `Vector{Any}` y obtener los elementos de ese contenedor cuando sea necesario, o incluso crear una variable global por puntero usando

```c
jl_module_t *mod = jl_main_module;
jl_sym_t *var = jl_symbol("var");
jl_binding_t *bp = jl_get_binding_wr(mod, var, 1);
jl_checked_assignment(bp, mod, var, val);
```

### Updating fields of GC-managed objects

El recolector de basura también opera bajo la suposición de que es consciente de cada objeto de generación anterior que apunta a uno de generación más joven. Cada vez que un puntero se actualiza rompiendo esa suposición, debe ser señalado al recolector con la función `jl_gc_wb` (barrera de escritura) de la siguiente manera:

```c
jl_value_t *parent = some_old_value, *child = some_young_value;
((some_specific_type*)parent)->field = child;
jl_gc_wb(parent, child);
```

En general, es imposible predecir qué valores estarán obsoletos en tiempo de ejecución, por lo que la barrera de escritura debe insertarse después de todas las asignaciones explícitas. Una excepción notable es si el objeto `parent` acaba de ser asignado y no se ha ejecutado ninguna recolección de basura desde entonces. Tenga en cuenta que la mayoría de las funciones `jl_...` a veces pueden invocar la recolección de basura.

La barrera de escritura también es necesaria para los arreglos de punteros al actualizar sus datos directamente. Llamar a `jl_array_ptr_set` es generalmente mucho más preferido. Pero se pueden hacer actualizaciones directas. Por ejemplo:

```c
jl_array_t *some_array = ...; // e.g. a Vector{Any}
void **data = jl_array_data(some_array, void*);
jl_value_t *some_value = ...;
data[0] = some_value;
jl_gc_wb(jl_array_owner(some_array), some_value);
```

### Controlling the Garbage Collector

Hay algunas funciones para controlar el GC. En casos de uso normales, estas no deberían ser necesarias.

| Function             | Description                                  |
|:-------------------- |:-------------------------------------------- |
| `jl_gc_collect()`    | Force a GC run                               |
| `jl_gc_enable(0)`    | Disable the GC, return previous state as int |
| `jl_gc_enable(1)`    | Enable the GC,  return previous state as int |
| `jl_gc_is_enabled()` | Return current state as int                  |

## Working with Arrays

Julia y C pueden compartir datos de arreglos sin copiar. El siguiente ejemplo mostrará cómo funciona esto.

Los arreglos de Julia se representan en C mediante el tipo de dato `jl_array_t*`. Básicamente, `jl_array_t` es una estructura que contiene:

  * Información sobre el tipo de dato
  * Un puntero al bloque de datos
  * Información sobre los tamaños del arreglo

Para mantener las cosas simples, comenzamos con un arreglo unidimensional. Crear un arreglo que contenga elementos Float64 de longitud 10 se puede hacer así:

```c
jl_value_t* array_type = jl_apply_array_type((jl_value_t*)jl_float64_type, 1);
jl_array_t* x          = jl_alloc_array_1d(array_type, 10);
```

Alternativamente, si ya has asignado el arreglo, puedes generar un envoltorio delgado alrededor de sus datos:

```c
double *existingArray = (double*)malloc(sizeof(double)*10);
jl_array_t *x = jl_ptr_to_array_1d(array_type, existingArray, 10, 0);
```

El último argumento es un booleano que indica si Julia debe tomar posesión de los datos. Si este argumento es distinto de cero, el GC llamará a `free` en el puntero de datos cuando el array ya no esté referenciado.

Para acceder a los datos de `x`, podemos usar `jl_array_data`:

```c
double *xData = jl_array_data(x, double);
```

Ahora podemos llenar el arreglo:

```c
for (size_t i = 0; i < jl_array_nrows(x); i++)
    xData[i] = i;
```

Ahora llamemos a una función de Julia que realiza una operación en su lugar en `x`:

```c
jl_function_t *func = jl_get_function(jl_base_module, "reverse!");
jl_call1(func, (jl_value_t*)x);
```

Al imprimir el arreglo, se puede verificar que los elementos de `x` ahora están invertidos.

### Accessing Returned Arrays

Si una función de Julia devuelve un array, el valor de retorno de `jl_eval_string` y `jl_call` se puede convertir a un `jl_array_t*`:

```c
jl_function_t *func  = jl_get_function(jl_base_module, "reverse");
jl_array_t *y = (jl_array_t*)jl_call1(func, (jl_value_t*)x);
```

Ahora el contenido de `y` se puede acceder como antes usando `jl_array_data`. Como siempre, asegúrate de mantener una referencia al arreglo mientras esté en uso.

### Multidimensional Arrays

Los arreglos multidimensionales de Julia se almacenan en memoria en orden de columna. Aquí hay un código que crea un arreglo 2D y accede a sus propiedades:

```c
// Create 2D array of float64 type
jl_value_t *array_type = jl_apply_array_type((jl_value_t*)jl_float64_type, 2);
int dims[] = {10,5};
jl_array_t *x  = jl_alloc_array_nd(array_type, dims, 2);

// Get array pointer
double *p = jl_array_data(x, double);
// Get number of dimensions
int ndims = jl_array_ndims(x);
// Get the size of the i-th dim
size_t size0 = jl_array_dim(x,0);
size_t size1 = jl_array_dim(x,1);

// Fill array with data
for(size_t i=0; i<size1; i++)
    for(size_t j=0; j<size0; j++)
        p[j + size0*i] = i + j;
```

Tenga en cuenta que, mientras que los arreglos de Julia utilizan indexación basada en 1, la API de C utiliza indexación basada en 0 (por ejemplo, al llamar a `jl_array_dim`) para que se lea como código C idiomático.

## Exceptions

El código de Julia puede lanzar excepciones. Por ejemplo, considera:

```c
jl_eval_string("this_function_does_not_exist()");
```

Esta llamada parecerá no hacer nada. Sin embargo, es posible verificar si se lanzó una excepción:

```c
if (jl_exception_occurred())
    printf("%s \n", jl_typeof_str(jl_exception_occurred()));
```

Si estás utilizando la API C de Julia desde un lenguaje que soporta excepciones (por ejemplo, Python, C#, C++), tiene sentido envolver cada llamada a `libjulia` con una función que verifique si se lanzó una excepción y luego vuelva a lanzar la excepción en el lenguaje anfitrión.

### Throwing Julia Exceptions

Al escribir funciones llamables en Julia, puede ser necesario validar los argumentos y lanzar excepciones para indicar errores. Una verificación de tipo típica se ve así:

```c
if (!jl_typeis(val, jl_float64_type)) {
    jl_type_error(function_name, (jl_value_t*)jl_float64_type, val);
}
```

Las excepciones generales se pueden generar utilizando las funciones:

```c
void jl_error(const char *str);
void jl_errorf(const char *fmt, ...);
```

`jl_error` toma una cadena C, y `jl_errorf` se llama como `printf`:

```c
jl_errorf("argument x = %d is too large", x);
```

donde en este ejemplo `x` se asume que es un entero.

### Thread-safety

En general, la API de C de Julia no es completamente segura para hilos. Al incrustar Julia en una aplicación multihilo, se debe tener cuidado de no violar las siguientes restricciones:

  * `jl_init()` solo puede ser llamado una vez en la vida de la aplicación. Lo mismo se aplica a `jl_atexit_hook()`, y solo puede ser llamado después de `jl_init()`.
  * Las funciones de la API `jl_...()` solo pueden ser llamadas desde el hilo en el que se llamó a `jl_init()`, *o desde hilos iniciados por el tiempo de ejecución de Julia*. Llamar a funciones de la API de Julia desde hilos iniciados por el usuario no está soportado y puede llevar a un comportamiento indefinido y a fallos.

La segunda condición anterior implica que no puedes llamar de manera segura a las funciones `jl_...()` desde hilos que no fueron iniciados por Julia (siendo la excepción el hilo que llama a `jl_init()`). Por ejemplo, lo siguiente no es compatible y probablemente causará un fallo de segmentación:

```c
void *func(void*)
{
    // Wrong, jl_eval_string() called from thread that was not started by Julia
    jl_eval_string("println(Threads.threadid())");
    return NULL;
}

int main()
{
    pthread_t t;

    jl_init();

    // Start a new thread
    pthread_create(&t, NULL, func, NULL);
    pthread_join(t, NULL);

    jl_atexit_hook(0);
}
```

En su lugar, realizar todas las llamadas de Julia desde el mismo hilo creado por el usuario funcionará:

```c
void *func(void*)
{
    // Okay, all jl_...() calls from the same thread,
    // even though it is not the main application thread
    jl_init();
    jl_eval_string("println(Threads.threadid())");
    jl_atexit_hook(0);
    return NULL;
}

int main()
{
    pthread_t t;
    // Create a new thread, which runs func()
    pthread_create(&t, NULL, func, NULL);
    pthread_join(t, NULL);
}
```

Un ejemplo de llamar a la API de C de Julia desde un hilo iniciado por Julia mismo:

```c
#include <julia/julia.h>
JULIA_DEFINE_FAST_TLS

double c_func(int i)
{
    printf("[C %08x] i = %d\n", pthread_self(), i);

    // Call the Julia sqrt() function to compute the square root of i, and return it
    jl_function_t *sqrt = jl_get_function(jl_base_module, "sqrt");
    jl_value_t* arg = jl_box_int32(i);
    double ret = jl_unbox_float64(jl_call1(sqrt, arg));

    return ret;
}

int main()
{
    jl_init();

    // Define a Julia function func() that calls our c_func() defined in C above
    jl_eval_string("func(i) = ccall(:c_func, Float64, (Int32,), i)");

    // Call func() multiple times, using multiple threads to do so
    jl_eval_string("println(Threads.threadpoolsize())");
    jl_eval_string("use(i) = println(\"[J $(Threads.threadid())] i = $(i) -> $(func(i))\")");
    jl_eval_string("Threads.@threads for i in 1:5 use(i) end");

    jl_atexit_hook(0);
}
```

Si ejecutamos este código con 2 hilos de Julia, obtenemos la siguiente salida (nota: la salida variará según la ejecución y el sistema):

```sh
$ JULIA_NUM_THREADS=2 ./thread_example
2
[C 3bfd9c00] i = 1
[C 23938640] i = 4
[J 1] i = 1 -> 1.0
[C 3bfd9c00] i = 2
[J 1] i = 2 -> 1.4142135623730951
[C 3bfd9c00] i = 3
[J 2] i = 4 -> 2.0
[C 23938640] i = 5
[J 1] i = 3 -> 1.7320508075688772
[J 2] i = 5 -> 2.23606797749979
```

Como se puede ver, el hilo 1 de Julia corresponde al ID de pthread 3bfd9c00, y el hilo 2 de Julia corresponde al ID 23938640, lo que muestra que, de hecho, se utilizan múltiples hilos a nivel de C, y que podemos llamar de manera segura a las rutinas de la API de C de Julia desde esos hilos.
