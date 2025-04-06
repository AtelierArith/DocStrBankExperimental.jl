# Calling C and Fortran Code

Aunque la mayoría del código se puede escribir en Julia, ya existen muchas bibliotecas de alta calidad y maduras para la computación numérica escritas en C y Fortran. Para permitir el uso fácil de este código existente, Julia facilita la llamada a funciones de C y Fortran de manera simple y eficiente. Julia tiene una filosofía de "sin código adicional": las funciones se pueden llamar directamente desde Julia sin ningún código "pegamento", generación de código o compilación, incluso desde el prompt interactivo. Esto se logra simplemente haciendo una llamada apropiada con el macro [`@ccall`](@ref) (o la sintaxis menos conveniente [`ccall`](@ref), ver el [`ccall` syntax section](@ref ccall-interface)).

El código que se debe llamar debe estar disponible como una biblioteca compartida. La mayoría de las bibliotecas de C y Fortran se envían compiladas como bibliotecas compartidas ya, pero si estás compilando el código tú mismo usando GCC (o Clang), necesitarás usar las opciones `-shared` y `-fPIC`. Las instrucciones de máquina generadas por el JIT de Julia son las mismas que una llamada nativa de C, por lo que la sobrecarga resultante es la misma que llamar a una función de biblioteca desde código C. [^1]

Por defecto, los compiladores de Fortran [generate mangled names](https://en.wikipedia.org/wiki/Name_mangling#Fortran) (por ejemplo, convirtiendo los nombres de las funciones a minúsculas o mayúsculas, a menudo añadiendo un guion bajo), y así para llamar a una función de Fortran debes pasar el identificador mangled correspondiente a la regla seguida por tu compilador de Fortran. Además, al llamar a una función de Fortran, todas las entradas deben pasarse como punteros a valores asignados en el heap o en la pila. Esto se aplica no solo a arreglos y otros objetos mutables que normalmente se asignan en el heap, sino también a valores escalares como enteros y flotantes que normalmente se asignan en la pila y se pasan comúnmente en registros al usar convenciones de llamada de C o Julia.

La sintaxis para [`@ccall`](@ref) para generar una llamada a la función de la biblioteca es:

```julia
  @ccall library.function_name(argvalue1::argtype1, ...)::returntype
  @ccall function_name(argvalue1::argtype1, ...)::returntype
  @ccall $function_pointer(argvalue1::argtype1, ...)::returntype
```

donde `library` es una constante o literal de cadena (pero ver [Non-constant Function Specifications](@ref) a continuación). La biblioteca puede ser omitida, en cuyo caso el nombre de la función se resuelve en el proceso actual. Esta forma se puede usar para llamar a funciones de la biblioteca C, funciones en el tiempo de ejecución de Julia, o funciones en una aplicación vinculada a Julia. También se puede especificar la ruta completa a la biblioteca. Alternativamente, `@ccall` también se puede usar para llamar a un puntero de función `$function_pointer`, como uno devuelto por `Libdl.dlsym`. Los `argtype`s corresponden a la firma de la función C y los `argvalue`s son los valores de argumento reales que se pasarán a la función.

!!! note
    Vea a continuación cómo [map C types to Julia types](@ref mapping-c-types-to-julia).


Como un ejemplo completo pero simple, lo siguiente llama a la función `clock` de la biblioteca estándar de C en la mayoría de los sistemas derivados de Unix:

```julia-repl
julia> t = @ccall clock()::Int32
2292761

julia> typeof(t)
Int32
```

`clock` no toma argumentos y devuelve un `Int32`. Para llamar a la función `getenv` y obtener un puntero al valor de una variable de entorno, se hace una llamada como esta:

```julia-repl
julia> path = @ccall getenv("SHELL"::Cstring)::Cstring
Cstring(@0x00007fff5fbffc45)

julia> unsafe_string(path)
"/bin/bash"
```

En la práctica, especialmente al proporcionar funcionalidad reutilizable, generalmente se envuelven los usos de `@ccall` en funciones de Julia que configuran los argumentos y luego verifican errores de la manera que especifique la función de C o Fortran. Y si ocurre un error, se lanza como una excepción normal de Julia. Esto es especialmente importante ya que las API de C y Fortran son notoriamente inconsistentes sobre cómo indican las condiciones de error. Por ejemplo, la función de la biblioteca C `getenv` está envuelta en la siguiente función de Julia, que es una versión simplificada de la definición real de [`env.jl`](https://github.com/JuliaLang/julia/blob/master/base/env.jl):

```julia
function getenv(var::AbstractString)
    val = @ccall getenv(var::Cstring)::Cstring
    if val == C_NULL
        error("getenv: undefined variable: ", var)
    end
    return unsafe_string(val)
end
```

La función `getenv` de C indica un error devolviendo `C_NULL`, pero otras funciones estándar de C indican errores de diferentes maneras, incluyendo devolver -1, 0, 1 y otros valores especiales. Este envoltorio lanza una excepción que indica el problema si el llamador intenta obtener una variable de entorno que no existe:

```julia-repl
julia> getenv("SHELL")
"/bin/bash"

julia> getenv("FOOBAR")
ERROR: getenv: undefined variable: FOOBAR
```

Aquí hay un ejemplo ligeramente más complejo que descubre el nombre del host de la máquina local.

```julia
function gethostname()
    hostname = Vector{UInt8}(undef, 256) # MAXHOSTNAMELEN
    err = @ccall gethostname(hostname::Ptr{UInt8}, sizeof(hostname)::Csize_t)::Int32
    Base.systemerror("gethostname", err != 0)
    hostname[end] = 0 # ensure null-termination
    return GC.@preserve hostname unsafe_string(pointer(hostname))
end
```

Este ejemplo primero asigna un arreglo de bytes. Luego llama a la función de la biblioteca C `gethostname` para llenar el arreglo con el nombre del host. Finalmente, toma un puntero al búfer del nombre del host y convierte el puntero a una cadena de Julia, asumiendo que es una cadena C terminada en nulo.

Es común que las bibliotecas C utilicen este patrón que requiere que el llamador asigne memoria para ser pasada al llamado y poblada. La asignación de memoria desde Julia de esta manera se logra generalmente creando un arreglo no inicializado y pasando un puntero a sus datos a la función C. Por eso no usamos el tipo `Cstring` aquí: como el arreglo está no inicializado, podría contener bytes nulos. Convertir a un `Cstring` como parte del `@ccall` verifica si hay bytes nulos contenidos y, por lo tanto, podría lanzar un error de conversión.

Desreferenciar `pointer(hostname)` con `unsafe_string` es una operación insegura ya que requiere acceso a la memoria asignada para `hostname` que puede haber sido recolectada como basura en el ínterin. El macro [`GC.@preserve`](@ref) previene que esto ocurra y, por lo tanto, evita el acceso a una ubicación de memoria inválida.

Finalmente, aquí hay un ejemplo de especificar una biblioteca a través de una ruta. Creamos una biblioteca compartida con el siguiente contenido

```c
#include <stdio.h>

void say_y(int y)
{
    printf("Hello from C: got y = %d.\n", y);
}
```

y compílalo con `gcc -fPIC -shared -o mylib.so mylib.c`. Luego se puede llamar especificando la ruta (absoluta) como el nombre de la biblioteca:

```julia-repl
julia> @ccall "./mylib.so".say_y(5::Cint)::Cvoid
Hello from C: got y = 5.
```

## Creating C-Compatible Julia Function Pointers

Es posible pasar funciones de Julia a funciones nativas de C que aceptan argumentos de puntero a función. Por ejemplo, para coincidir con los prototipos de C de la forma:

```c
typedef returntype (*functiontype)(argumenttype, ...)
```

El macro [`@cfunction`](@ref) genera el puntero de función compatible con C para una llamada a una función de Julia. Los argumentos para `4d61726b646f64652822222c2022406366756e6374696f6e2229_40726566` son:

1. Una función de Julia
2. El tipo de retorno de la función
3. Una tupla de tipos de entrada, correspondiente a la firma de la función

!!! note
    Al igual que con `@ccall`, el tipo de retorno y los tipos de entrada deben ser constantes literales.


!!! note
    Actualmente, solo se admite la convención de llamada C predeterminada de la plataforma. Esto significa que los punteros generados por `@cfunction` no se pueden utilizar en llamadas donde WINAPI espera una función `stdcall` en Windows de 32 bits, pero se pueden utilizar en WIN64 (donde `stdcall` se unifica con la convención de llamada C).


!!! note
    Las funciones de callback expuestas a través de `@cfunction` no deben lanzar errores, ya que eso devolverá el control al tiempo de ejecución de Julia de manera inesperada y puede dejar el programa en un estado indefinido.


Un ejemplo clásico es la función `qsort` de la biblioteca estándar de C, declarada como:

```c
void qsort(void *base, size_t nitems, size_t size,
           int (*compare)(const void*, const void*));
```

El argumento `base` es un puntero a un arreglo de longitud `nitems`, con elementos de `size` bytes cada uno. `compare` es una función de callback que toma punteros a dos elementos `a` y `b` y devuelve un entero menor/mayor que cero si `a` debe aparecer antes/después de `b` (o cero si se permite cualquier orden).

Ahora, supongamos que tenemos un arreglo unidimensional `A` de valores en Julia que queremos ordenar utilizando la función `qsort` (en lugar de la función `sort` incorporada de Julia). Antes de considerar llamar a `qsort` y pasar argumentos, necesitamos escribir una función de comparación:

```jldoctest mycompare
julia> function mycompare(a, b)::Cint
           return (a < b) ? -1 : ((a > b) ? +1 : 0)
       end;
```

`qsort` espera una función de comparación que devuelva un `int` de C, por lo que anotamos el tipo de retorno como `Cint`.

Para pasar esta función a C, obtenemos su dirección utilizando el macro `@cfunction`:

```jldoctest mycompare
julia> mycompare_c = @cfunction(mycompare, Cint, (Ref{Cdouble}, Ref{Cdouble}));
```

[`@cfunction`](@ref) requiere tres argumentos: la función de Julia (`mycompare`), el tipo de retorno (`Cint`), y una tupla literal de los tipos de argumentos de entrada, en este caso para ordenar un arreglo de elementos `Cdouble` ([`Float64`](@ref)).

La llamada final a `qsort` se ve así:

```jldoctest mycompare
julia> A = [1.3, -2.7, 4.4, 3.1];

julia> @ccall qsort(A::Ptr{Cdouble}, length(A)::Csize_t, sizeof(eltype(A))::Csize_t, mycompare_c::Ptr{Cvoid})::Cvoid

julia> A
4-element Vector{Float64}:
 -2.7
  1.3
  3.1
  4.4
```

Como muestra el ejemplo, el arreglo original de Julia `A` ahora ha sido ordenado: `[-2.7, 1.3, 3.1, 4.4]`. Tenga en cuenta que Julia [takes care of converting the array to a `Ptr{Cdouble}`](@ref automatic-type-conversion)), calculando el tamaño del tipo de elemento en bytes, y así sucesivamente.

Para divertirte, intenta insertar una línea `println("mycompare($a, $b)")` en `mycompare`, lo que te permitirá ver las comparaciones que `qsort` está realizando (y verificar que realmente está llamando a la función de Julia que le pasaste).

## [Mapping C Types to Julia](@id mapping-c-types-to-julia)

Es crítico que el tipo C declarado coincida exactamente con su declaración en Julia. Las inconsistencias pueden causar que el código que funciona correctamente en un sistema falle o produzca resultados indeterminados en un sistema diferente.

Tenga en cuenta que no se utilizan archivos de encabezado de C en ninguna parte del proceso de llamada a funciones de C: usted es responsable de asegurarse de que sus tipos de Julia y las firmas de llamada reflejen con precisión los de el archivo de encabezado de C.[^2]

### [Automatic Type Conversion](@id automatic-type-conversion)

Julia inserta automáticamente llamadas a la función [`Base.cconvert`](@ref) para convertir cada argumento al tipo especificado. Por ejemplo, la siguiente llamada:

```julia
@ccall "libfoo".foo(x::Int32, y::Float64)::Cvoid
```

se comportará como si estuviera escrito así:

```julia
c_x = Base.cconvert(Int32, x)
c_y = Base.cconvert(Float64, y)
GC.@preserve c_x c_y begin
    @ccall "libfoo".foo(
        Base.unsafe_convert(Int32, c_x)::Int32,
        Base.unsafe_convert(Float64, c_y)::Float64
    )::Cvoid
end
```

[`Base.cconvert`](@ref) normalmente solo llama a [`convert`](@ref), pero se puede definir para devolver un nuevo objeto arbitrario más apropiado para pasar a C. Esto debe usarse para realizar todas las asignaciones de memoria que serán accedidas por el código C. Por ejemplo, esto se utiliza para convertir un `Array` de objetos (por ejemplo, cadenas) en un array de punteros.

[`Base.unsafe_convert`](@ref) maneja la conversión a [`Ptr`](@ref) tipos. Se considera inseguro porque convertir un objeto a un puntero nativo puede ocultar el objeto del recolector de basura, lo que provoca que se libere prematuramente.

### Type Correspondences

Primero, revisemos alguna terminología relevante de tipos en Julia:

| Syntax / Keyword        | Example                                    | Description                                                                                                                                                                                                                                                       |
|:----------------------- |:------------------------------------------ |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `mutable struct`        | `BitSet`                                   | "Leaf Type" :: A group of related data that includes a type-tag, is managed by the Julia GC, and is defined by object-identity. The type parameters of a leaf type must be fully defined (no `TypeVars` are allowed) in order for the instance to be constructed. |
| `abstract type`         | `Any`, `AbstractArray{T, N}`, `Complex{T}` | "Super Type" :: A super-type (not a leaf-type) that cannot be instantiated, but can be used to describe a group of types.                                                                                                                                         |
| `T{A}`                  | `Vector{Int}`                              | "Type Parameter" :: A specialization of a type (typically used for dispatch or storage optimization).                                                                                                                                                             |
|                         |                                            | "TypeVar" :: The `T` in the type parameter declaration is referred to as a TypeVar (short for type variable).                                                                                                                                                     |
| `primitive type`        | `Int`, `Float64`                           | "Primitive Type" :: A type with no fields, but a size. It is stored and defined by-value.                                                                                                                                                                         |
| `struct`                | `Pair{Int, Int}`                           | "Struct" :: A type with all fields defined to be constant. It is defined by-value, and may be stored with a type-tag.                                                                                                                                             |
|                         | `ComplexF64` (`isbits`)                    | "Is-Bits"   :: A `primitive type`, or a `struct` type where all fields are other `isbits` types. It is defined by-value, and is stored without a type-tag.                                                                                                        |
| `struct ...; end`       | `nothing`                                  | "Singleton" :: a Leaf Type or Struct with no fields.                                                                                                                                                                                                              |
| `(...)` or `tuple(...)` | `(1, 2, 3)`                                | "Tuple" :: an immutable data-structure similar to an anonymous struct type, or a constant array. Represented as either an array or a struct.                                                                                                                      |

### [Bits Types](@id man-bits-types)

Hay varios tipos especiales de los que hay que estar al tanto, ya que ningún otro tipo puede definirse para comportarse de la misma manera:

  * `Float32`

    Corresponde exactamente al tipo `float` en C (o `REAL*4` en Fortran).
  * `Float64`

    Corresponde exactamente al tipo `double` en C (o `REAL*8` en Fortran).
  * `ComplejoF32`

    Corresponde exactamente al tipo `complex float` en C (o `COMPLEX*8` en Fortran).
  * `ComplejoF64`

    Corresponde exactamente al tipo `complex double` en C (o `COMPLEX*16` en Fortran).
  * `Firmado`

    Corresponde exactamente a la anotación de tipo `signed` en C (o cualquier tipo `INTEGER` en Fortran). Se asume que cualquier tipo de Julia que no sea un subtipo de [`Signed`](@ref) es sin signo.

  * `Ref{T}`

    Se comporta como un `Ptr{T}` que puede gestionar su memoria a través del GC de Julia.

  * `Array{T,N}`

    Cuando un arreglo se pasa a C como un argumento `Ptr{T}`, no se realiza una reinterpretación: Julia requiere que el tipo de elemento del arreglo coincida con `T`, y se pasa la dirección del primer elemento.

    Por lo tanto, si un `Array` contiene datos en el formato incorrecto, deberá ser convertido explícitamente utilizando una llamada como `trunc.(Int32, A)`.

    Para pasar un arreglo `A` como un puntero de un tipo diferente *sin* convertir los datos de antemano (por ejemplo, para pasar un arreglo de `Float64` a una función que opera sobre bytes no interpretados), puedes declarar el argumento como `Ptr{Cvoid}`.

    Si se pasa un arreglo de tipo `Ptr{T}` como un argumento de tipo `Ptr{Ptr{T}}`, [`Base.cconvert`](@ref) intentará primero hacer una copia terminada en nulo del arreglo con cada elemento reemplazado por su versión `4d61726b646f776e2e436f64652822222c2022426173652e63636f6e766572742229_40726566`. Esto permite, por ejemplo, pasar un arreglo de punteros `argv` de tipo `Vector{String}` a un argumento de tipo `Ptr{Ptr{Cchar}}`.

En todos los sistemas que actualmente soportamos, los tipos de valor básicos de C/C++ pueden ser traducidos a tipos de Julia de la siguiente manera. Cada tipo de C también tiene un tipo correspondiente en Julia con el mismo nombre, precedido por C. Esto puede ayudar al escribir código portátil (y recordar que un `int` en C no es lo mismo que un `Int` en Julia).

**Tipos Independientes del Sistema**

| C name                                                  | Fortran name             | Standard Julia Alias | Julia Base Type                                                                                             |
|:------------------------------------------------------- |:------------------------ |:-------------------- |:----------------------------------------------------------------------------------------------------------- |
| `unsigned char`                                         | `CHARACTER`              | `Cuchar`             | `UInt8`                                                                                                     |
| `bool` (_Bool in C99+)                                  |                          | `Cuchar`             | `UInt8`                                                                                                     |
| `short`                                                 | `INTEGER*2`, `LOGICAL*2` | `Cshort`             | `Int16`                                                                                                     |
| `unsigned short`                                        |                          | `Cushort`            | `UInt16`                                                                                                    |
| `int`, `BOOL` (C, typical)                              | `INTEGER*4`, `LOGICAL*4` | `Cint`               | `Int32`                                                                                                     |
| `unsigned int`                                          |                          | `Cuint`              | `UInt32`                                                                                                    |
| `long long`                                             | `INTEGER*8`, `LOGICAL*8` | `Clonglong`          | `Int64`                                                                                                     |
| `unsigned long long`                                    |                          | `Culonglong`         | `UInt64`                                                                                                    |
| `intmax_t`                                              |                          | `Cintmax_t`          | `Int64`                                                                                                     |
| `uintmax_t`                                             |                          | `Cuintmax_t`         | `UInt64`                                                                                                    |
| `float`                                                 | `REAL*4i`                | `Cfloat`             | `Float32`                                                                                                   |
| `double`                                                | `REAL*8`                 | `Cdouble`            | `Float64`                                                                                                   |
| `complex float`                                         | `COMPLEX*8`              | `ComplexF32`         | `Complex{Float32}`                                                                                          |
| `complex double`                                        | `COMPLEX*16`             | `ComplexF64`         | `Complex{Float64}`                                                                                          |
| `ptrdiff_t`                                             |                          | `Cptrdiff_t`         | `Int`                                                                                                       |
| `ssize_t`                                               |                          | `Cssize_t`           | `Int`                                                                                                       |
| `size_t`                                                |                          | `Csize_t`            | `UInt`                                                                                                      |
| `void`                                                  |                          |                      | `Cvoid`                                                                                                     |
| `void` and `[[noreturn]]` or `_Noreturn`                |                          |                      | `Union{}`                                                                                                   |
| `void*`                                                 |                          |                      | `Ptr{Cvoid}` (or similarly `Ref{Cvoid}`)                                                                    |
| `T*` (where T represents an appropriately defined type) |                          |                      | `Ref{T}` (T may be safely mutated only if T is an isbits type)                                              |
| `char*` (or `char[]`, e.g. a string)                    | `CHARACTER*N`            |                      | `Cstring` if null-terminated, or `Ptr{UInt8}` if not                                                        |
| `char**` (or `*char[]`)                                 |                          |                      | `Ptr{Ptr{UInt8}}`                                                                                           |
| `jl_value_t*` (any Julia Type)                          |                          |                      | `Any`                                                                                                       |
| `jl_value_t* const*` (a reference to a Julia value)     |                          |                      | `Ref{Any}` (const, since mutation would require a write barrier, which is not possible to insert correctly) |
| `va_arg`                                                |                          |                      | Not supported                                                                                               |
| `...` (variadic function specification)                 |                          |                      | `T...` (where `T` is one of the above types, when using the `ccall` function)                               |
| `...` (variadic function specification)                 |                          |                      | `; va_arg1::T, va_arg2::S, etc.` (only supported with `@ccall` macro)                                       |

El tipo [`Cstring`](@ref) es esencialmente un sinónimo de `Ptr{UInt8}`, excepto que la conversión a `Cstring` lanza un error si la cadena de Julia contiene caracteres nulos incrustados (lo que haría que la cadena se truncara silenciosamente si la rutina C trata el nulo como el terminador). Si estás pasando un `char*` a una rutina C que no asume la terminación nula (por ejemplo, porque pasas una longitud de cadena explícita), o si sabes con certeza que tu cadena de Julia no contiene nulos y quieres omitir la verificación, puedes usar `Ptr{UInt8}` como el tipo de argumento. `Cstring` también se puede usar como el tipo de retorno [`ccall`](@ref), pero en ese caso, obviamente no introduce ninguna verificación adicional y solo está destinado a mejorar la legibilidad de la llamada.

**Tipos Dependientes del Sistema**

| C name          | Standard Julia Alias | Julia Base Type                              |
|:--------------- |:-------------------- |:-------------------------------------------- |
| `char`          | `Cchar`              | `Int8` (x86, x86_64), `UInt8` (powerpc, arm) |
| `long`          | `Clong`              | `Int` (UNIX), `Int32` (Windows)              |
| `unsigned long` | `Culong`             | `UInt` (UNIX), `UInt32` (Windows)            |
| `wchar_t`       | `Cwchar_t`           | `Int32` (UNIX), `UInt16` (Windows)           |

!!! note
    Al llamar a Fortran, todas las entradas deben pasarse mediante punteros a valores asignados en el heap o en la pila, por lo que todas las correspondencias de tipo anteriores deben contener un envoltorio adicional `Ptr{..}` o `Ref{..}` alrededor de su especificación de tipo.


!!! warning
    Para argumentos de cadena (`char*`), el tipo de Julia debe ser `Cstring` (si se espera datos terminados en nulo), o bien `Ptr{Cchar}` o `Ptr{UInt8}` en caso contrario (estos dos tipos de puntero tienen el mismo efecto), como se describió anteriormente, no `String`. De manera similar, para argumentos de matriz (`T[]` o `T*`), el tipo de Julia debe ser nuevamente `Ptr{T}`, no `Vector{T}`.


!!! warning
    El tipo `Char` de Julia es de 32 bits, lo que no es lo mismo que el tipo de carácter ancho (`wchar_t` o `wint_t`) en todas las plataformas.


!!! warning
    Un tipo de retorno `Union{}` significa que la función no devolverá, es decir, `[[noreturn]]` de C++11 o `_Noreturn` de C11 (por ejemplo, `jl_throw` o `longjmp`). No utilices esto para funciones que no devuelven ningún valor (`void`) pero sí devuelven; para esas, utiliza `Cvoid` en su lugar.


!!! note
    Para los argumentos `wchar_t*`, el tipo de Julia debería ser [`Cwstring`](@ref) (si la rutina C espera una cadena terminada en nulo), o `Ptr{Cwchar_t}` de lo contrario. También ten en cuenta que los datos de cadena UTF-8 en Julia están internamente terminados en nulo, por lo que se pueden pasar a funciones C que esperan datos terminados en nulo sin hacer una copia (pero usar el tipo `Cwstring` causará que se lance un error si la cadena en sí contiene caracteres nulos).


!!! note
    Las funciones de C que toman un argumento de tipo `char**` se pueden llamar utilizando un tipo `Ptr{Ptr{UInt8}}` dentro de Julia. Por ejemplo, las funciones de C de la forma:

    ```c
    int main(int argc, char **argv);
    ```

    se puede llamar a través del siguiente código de Julia:

    ```julia
    argv = [ "a.out", "arg1", "arg2" ]
    @ccall main(length(argv)::Int32, argv::Ptr{Ptr{UInt8}})::Int32
    ```


!!! note
    Para las funciones de Fortran que toman cadenas de longitud variable de tipo `character(len=*)`, las longitudes de las cadenas se proporcionan como *argumentos ocultos*. El tipo y la posición de estos argumentos en la lista son específicos del compilador, donde los proveedores de compiladores generalmente utilizan `Csize_t` como tipo y añaden los argumentos ocultos al final de la lista de argumentos. Mientras que este comportamiento es fijo para algunos compiladores (GNU), otros *opcionalmente* permiten colocar argumentos ocultos directamente después del argumento de carácter (Intel, PGI). Por ejemplo, las subrutinas de Fortran de la forma

    ```fortran
    subroutine test(str1, str2)
    character(len=*) :: str1,str2
    ```

    se puede llamar a través del siguiente código de Julia, donde se añaden las longitudes

    ```julia
    str1 = "foo"
    str2 = "bar"
    ccall(:test, Cvoid, (Ptr{UInt8}, Ptr{UInt8}, Csize_t, Csize_t),
                        str1, str2, sizeof(str1), sizeof(str2))
    ```


!!! warning
    Los compiladores de Fortran *pueden* también agregar otros argumentos ocultos para punteros, arreglos de forma asumida (`:`) y arreglos de tamaño asumido (`*`). Este comportamiento se puede evitar utilizando `ISO_C_BINDING` e incluyendo `bind(c)` en la definición de la subrutina, lo cual se recomienda encarecidamente para código interoperable. En este caso, no habrá argumentos ocultos, a costa de algunas características del lenguaje (por ejemplo, solo se permitirá `character(len=1)` para pasar cadenas).


!!! note
    Una función de C declarada para devolver `Cvoid` devolverá el valor `nothing` en Julia.


### Struct Type Correspondences

Los tipos compuestos como `struct` en C o `TYPE` en Fortran90 (o `STRUCTURE` / `RECORD` en algunas variantes de F77) se pueden reflejar en Julia creando una definición de `struct` con el mismo diseño de campos.

Cuando se utilizan de forma recursiva, los tipos `isbits` se almacenan en línea. Todos los demás tipos se almacenan como un puntero a los datos. Al reflejar una estructura utilizada por valor dentro de otra estructura en C, es imperativo que no intentes copiar manualmente los campos, ya que esto no preservará la alineación correcta de los campos. En su lugar, declara un tipo de estructura `isbits` y utiliza eso en su lugar. Las estructuras sin nombre no son posibles en la traducción a Julia.

Las declaraciones de estructuras y uniones empaquetadas no son compatibles con Julia.

Puedes obtener una aproximación de un `union` si conoces, a priori, el campo que tendrá el mayor tamaño (potencialmente incluyendo relleno). Al traducir tus campos a Julia, declara el campo de Julia como solo de ese tipo.

Los arreglos de parámetros se pueden expresar con `NTuple`. Por ejemplo, la estructura en notación C se escribe como

```c
struct B {
    int A[3];
};

b_a_2 = B.A[2];
```

puede escribirse en Julia como

```julia
struct B
    A::NTuple{3, Cint}
end

b_a_2 = B.A[3]  # note the difference in indexing (1-based in Julia, 0-based in C)
```

Los arreglos de tamaño desconocido (estructuras de longitud variable compatibles con C99 especificadas por `[]` o `[0]`) no son compatibles directamente. A menudo, la mejor manera de manejar esto es tratar con los desplazamientos de bytes directamente. Por ejemplo, si una biblioteca de C declara un tipo de cadena adecuado y devuelve un puntero a él:

```c
struct String {
    int strlen;
    char data[];
};
```

En Julia, podemos acceder a las partes de forma independiente para hacer una copia de esa cadena:

```julia
str = from_c::Ptr{Cvoid}
len = unsafe_load(Ptr{Cint}(str))
unsafe_string(str + Core.sizeof(Cint), len)
```

### Type Parameters

Los argumentos de tipo para `@ccall` y `@cfunction` se evalúan estáticamente, cuando se define el método que contiene el uso. Por lo tanto, deben tener la forma de una tupla literal, no de una variable, y no pueden hacer referencia a variables locales.

Esta puede sonar como una restricción extraña, pero recuerda que dado que C no es un lenguaje dinámico como Julia, sus funciones solo pueden aceptar tipos de argumentos con una firma fija y conocida estáticamente.

Sin embargo, aunque el diseño del tipo debe conocerse de manera estática para calcular el ABI de C previsto, los parámetros estáticos de la función se consideran parte de este entorno estático. Los parámetros estáticos de la función pueden usarse como parámetros de tipo en la firma de llamada, siempre que no afecten el diseño del tipo. Por ejemplo, `f(x::T) where {T} = @ccall valid(x::Ptr{T})::Ptr{T}` es válido, ya que `Ptr` es siempre un tipo primitivo de tamaño de palabra. Pero, `g(x::T) where {T} = @ccall notvalid(x::T)::T` no es válido, ya que el diseño del tipo de `T` no se conoce de manera estática.

### SIMD Values

Nota: Esta función está actualmente implementada solo en plataformas de 64 bits x86 y AArch64.

Si una rutina de C/C++ tiene un argumento o un valor de retorno que es un tipo SIMD nativo, el tipo correspondiente en Julia es una tupla homogénea de `VecElement` que se mapea naturalmente al tipo SIMD. Específicamente:

>   * La tupla debe tener el mismo tamaño que el tipo SIMD. Por ejemplo, una tupla que represente un `__m128` en x86 debe tener un tamaño de 16 bytes.
>   * El tipo de elemento de la tupla debe ser una instancia de `VecElement{T}` donde `T` es un tipo primitivo que tiene 1, 2, 4 u 8 bytes.


Por ejemplo, considera esta rutina en C que utiliza intrínsecos de AVX:

```c
#include <immintrin.h>

__m256 dist( __m256 a, __m256 b ) {
    return _mm256_sqrt_ps(_mm256_add_ps(_mm256_mul_ps(a, a),
                                        _mm256_mul_ps(b, b)));
}
```

El siguiente código de Julia llama a `dist` usando `ccall`:

```julia
const m256 = NTuple{8, VecElement{Float32}}

a = m256(ntuple(i -> VecElement(sin(Float32(i))), 8))
b = m256(ntuple(i -> VecElement(cos(Float32(i))), 8))

function call_dist(a::m256, b::m256)
    @ccall "libdist".dist(a::m256, b::m256)::m256
end

println(call_dist(a,b))
```

La máquina anfitriona debe tener los registros SIMD requeridos. Por ejemplo, el código anterior no funcionará en anfitriones sin soporte AVX.

### Memory Ownership

**`malloc`/`free`**

La asignación y desasignación de memoria de tales objetos debe ser manejada por llamadas a las rutinas de limpieza apropiadas en las bibliotecas que se están utilizando, al igual que en cualquier programa en C. No intente liberar un objeto recibido de una biblioteca C con [`Libc.free`](@ref) en Julia, ya que esto puede resultar en que la función `free` sea llamada a través de la biblioteca incorrecta y cause que el proceso se aborte. Lo inverso (pasar un objeto asignado en Julia para ser liberado por una biblioteca externa) es igualmente inválido.

### When to use `T`, `Ptr{T}` and `Ref{T}`

En el código de Julia que envuelve llamadas a rutinas externas de C, los datos ordinarios (no punteros) deben declararse como tipo `T` dentro del `@ccall`, ya que se pasan por valor. Para el código C que acepta punteros, [`Ref{T}`](@ref) debe usarse generalmente para los tipos de argumentos de entrada, permitiendo el uso de punteros a memoria gestionada tanto por Julia como por C a través de la llamada implícita a [`Base.cconvert`](@ref). En contraste, los punteros devueltos por la función C llamada deben declararse como del tipo de salida [`Ptr{T}`](@ref), reflejando que la memoria a la que se apunta es gestionada solo por C. Los punteros contenidos en estructuras C deben representarse como campos de tipo `Ptr{T}` dentro de los tipos de estructuras Julia correspondientes diseñados para imitar la estructura interna de las estructuras C correspondientes.

En el código de Julia que envuelve llamadas a rutinas externas de Fortran, todos los argumentos de entrada deben declararse como de tipo `Ref{T}`, ya que Fortran pasa todas las variables por punteros a ubicaciones de memoria. El tipo de retorno debe ser `Cvoid` para subrutinas de Fortran, o un `T` para funciones de Fortran que devuelven el tipo `T`.

## Mapping C Functions to Julia

### `@ccall` / `@cfunction` argument translation guide

Para traducir una lista de argumentos de C a Julia:

  * `T`, donde `T` es uno de los tipos primitivos: `char`, `int`, `long`, `short`, `float`, `double`, `complex`, `enum` o cualquiera de sus equivalentes `typedef`

      * `T`, donde `T` es un tipo de bits de Julia equivalente (según la tabla anterior)
      * si `T` es un `enum`, el tipo de argumento debe ser equivalente a `Cint` o `Cuint`
      * el valor del argumento será copiado (pasado por valor)
  * `struct T` (incluyendo typedef a una estructura)

      * `T`, donde `T` es un tipo hoja de Julia
      * el valor del argumento será copiado (pasado por valor)
  * `void*`

      * depende de cómo se use este parámetro, primero traduce esto al tipo de puntero previsto, luego determina el equivalente en Julia utilizando las reglas restantes de esta lista.
      * este argumento puede declararse como `Ptr{Cvoid}` si realmente es solo un puntero desconocido
  * `jl_value_t*`

      * `Cualquiera`
      * el valor del argumento debe ser un objeto de Julia válido
  * `jl_value_t* const*`

      * `Ref{Cualquiera}`
      * la lista de argumentos debe ser un objeto Julia válido (o `C_NULL`)
      * no se puede utilizar como un parámetro de salida, a menos que el usuario pueda organizar por separado que el objeto sea preservado por el GC
  * `T*`

      * `Ref{T}`, donde `T` es el tipo de Julia correspondiente a `T`
      * el valor del argumento se copiará si es de tipo `inlinealloc` (lo que incluye `isbits`; de lo contrario, el valor debe ser un objeto válido de Julia.
  * `T (*)(...)` (por ejemplo, un puntero a una función)

      * `Ptr{Cvoid}` (es posible que necesites usar [`@cfunction`](@ref) explícitamente para crear este puntero)
  * `...` (por ejemplo, un vararg)

      * [para `ccall`]: `T...`, donde `T` es el único tipo de Julia de todos los argumentos restantes
      * [para `@ccall`]: `; va_arg1::T, va_arg2::S, etc`, donde `T` y `S` son el tipo de Julia (es decir, separa los argumentos regulares de los varargs con un `;`)
      * actualmente no es compatible con `@cfunction`
  * `va_arg`

      * no soportado por `ccall` o `@cfunction`

### `@ccall` / `@cfunction` return type translation guide

Para traducir un tipo de retorno de C a Julia:

  * `vacío`

      * `Cvoid` (esto devolverá la instancia singleton `nothing::Cvoid`)
  * `T`, donde `T` es uno de los tipos primitivos: `char`, `int`, `long`, `short`, `float`, `double`, `complex`, `enum` o cualquiera de sus equivalentes `typedef`.

      * `T`, donde `T` es un tipo de bits de Julia equivalente (según la tabla anterior)
      * si `T` es un `enum`, el tipo de argumento debe ser equivalente a `Cint` o `Cuint`
      * el valor del argumento será copiado (devuelto por valor)
  * `struct T` (incluyendo typedef a una estructura)

      * `T`, donde `T` es un tipo de hoja de Julia
      * el valor del argumento será copiado (devuelto por valor)
  * `void*`

      * depende de cómo se use este parámetro, primero traduce esto al tipo de puntero previsto, luego determina el equivalente de Julia utilizando las reglas restantes de esta lista
      * este argumento puede ser declarado como `Ptr{Cvoid}` si realmente es solo un puntero desconocido
  * `jl_value_t*`

      * `Cualquiera`
      * el valor del argumento debe ser un objeto de Julia válido
  * `jl_value_t**`

      * `Ptr{Any}` (`Ref{Any}` no es un tipo de retorno válido)
  * `T*`

      * Si la memoria ya es propiedad de Julia, o es un tipo `isbits`, y se sabe que no es nula:

          * `Ref{T}`, donde `T` es el tipo de Julia correspondiente a `T`
          * un tipo de retorno de `Ref{Any}` es inválido, debería ser `Any` (correspondiente a `jl_value_t*`) o `Ptr{Any}` (correspondiente a `jl_value_t**`)
          * C **NO DEBE** modificar la memoria devuelta a través de `Ref{T}` si `T` es un tipo `isbits`
      * Si la memoria es propiedad de C:

          * `Ptr{T}`, donde `T` es el tipo de Julia correspondiente a `T`
  * `T (*)(...)` (por ejemplo, un puntero a una función)

      * `Ptr{Cvoid}` para llamar a esto directamente desde Julia, necesitarás pasarlo como el primer argumento a `@ccall`. Consulta [Indirect Calls](@ref).

### Passing Pointers for Modifying Inputs

Debido a que C no admite múltiples valores de retorno, a menudo las funciones de C tomarán punteros a datos que la función modificará. Para lograr esto dentro de un `@ccall`, primero necesitas encapsular el valor dentro de un [`Ref{T}`](@ref) del tipo apropiado. Cuando pases este objeto `Ref` como argumento, Julia pasará automáticamente un puntero C a los datos encapsulados:

```julia
width = Ref{Cint}(0)
range = Ref{Cfloat}(0)
@ccall foo(width::Ref{Cint}, range::Ref{Cfloat})::Cvoid
```

Al regresar, el contenido de `width` y `range` se puede recuperar (si fueron cambiados por `foo`) mediante `width[]` y `range[]`; es decir, actúan como arreglos de cero dimensiones.

## C Wrapper Examples

Comencemos con un ejemplo simple de un envoltorio en C que devuelve un tipo `Ptr`:

```julia
mutable struct gsl_permutation
end

# The corresponding C signature is
#     gsl_permutation * gsl_permutation_alloc (size_t n);
function permutation_alloc(n::Integer)
    output_ptr = @ccall "libgsl".gsl_permutation_alloc(n::Csize_t)::Ptr{gsl_permutation}
    if output_ptr == C_NULL # Could not allocate memory
        throw(OutOfMemoryError())
    end
    return output_ptr
end
```

El [GNU Scientific Library](https://www.gnu.org/software/gsl/) (aquí asumido como accesible a través de `:libgsl`) define un puntero opaco, `gsl_permutation *`, como el tipo de retorno de la función C `gsl_permutation_alloc`. Dado que el código del usuario nunca tiene que mirar dentro de la estructura `gsl_permutation`, el envoltorio correspondiente en Julia simplemente necesita una nueva declaración de tipo, `gsl_permutation`, que no tiene campos internos y cuyo único propósito es ser colocado en el parámetro de tipo de un tipo `Ptr`. El tipo de retorno de [`ccall`](@ref) se declara como `Ptr{gsl_permutation}`, ya que la memoria asignada y apuntada por `output_ptr` es controlada por C.

La entrada `n` se pasa por valor, por lo que la firma de entrada de la función se declara simplemente como `::Csize_t` sin necesidad de `Ref` o `Ptr`. (Si el envoltorio estuviera llamando a una función de Fortran en su lugar, la firma de entrada de la función correspondiente sería `::Ref{Csize_t}`, ya que las variables de Fortran se pasan por punteros). Además, `n` puede ser cualquier tipo que sea convertible a un entero `Csize_t`; el [`ccall`](@ref) llama implícitamente a [`Base.cconvert(Csize_t, n)`](@ref).

Aquí hay un segundo ejemplo que envuelve el destructor correspondiente:

```julia
# The corresponding C signature is
#     void gsl_permutation_free (gsl_permutation * p);
function permutation_free(p::Ptr{gsl_permutation})
    @ccall "libgsl".gsl_permutation_free(p::Ptr{gsl_permutation})::Cvoid
end
```

Aquí hay un tercer ejemplo pasando arreglos de Julia:

```julia
# The corresponding C signature is
#    int gsl_sf_bessel_Jn_array (int nmin, int nmax, double x,
#                                double result_array[])
function sf_bessel_Jn_array(nmin::Integer, nmax::Integer, x::Real)
    if nmax < nmin
        throw(DomainError())
    end
    result_array = Vector{Cdouble}(undef, nmax - nmin + 1)
    errorcode = @ccall "libgsl".gsl_sf_bessel_Jn_array(
                    nmin::Cint, nmax::Cint, x::Cdouble, result_array::Ref{Cdouble})::Cint
    if errorcode != 0
        error("GSL error code $errorcode")
    end
    return result_array
end
```

La función C `wrapped` devuelve un código de error entero; los resultados de la evaluación real de la función Bessel J llenan el arreglo de Julia `result_array`. Esta variable se declara como un `Ref{Cdouble}`, ya que su memoria es asignada y gestionada por Julia. La llamada implícita a [`Base.cconvert(Ref{Cdouble}, result_array)`](@ref) desempaqueta el puntero de Julia a una estructura de datos de arreglo de Julia en una forma comprensible por C.

## Fortran Wrapper Example

El siguiente ejemplo utiliza `ccall` para llamar a una función en una biblioteca Fortran común (libBLAS) para calcular un producto punto. Observe que el mapeo de argumentos es un poco diferente aquí que arriba, ya que necesitamos mapear de Julia a Fortran. En cada tipo de argumento, especificamos `Ref` o `Ptr`. Esta convención de mangling puede ser específica de su compilador Fortran y sistema operativo y es probable que no esté documentada. Sin embargo, envolver cada uno en un `Ref` (o `Ptr`, donde sea equivalente) es un requisito frecuente de las implementaciones de compiladores Fortran:

```julia
function compute_dot(DX::Vector{Float64}, DY::Vector{Float64})
    @assert length(DX) == length(DY)
    n = length(DX)
    incx = incy = 1
    product = @ccall "libLAPACK".ddot(
        n::Ref{Int32}, DX::Ptr{Float64}, incx::Ref{Int32}, DY::Ptr{Float64}, incy::Ref{Int32})::Float64
    return product
end
```

## Garbage Collection Safety

Al pasar datos a un `@ccall`, es mejor evitar usar la función [`pointer`](@ref). En su lugar, define un método [`Base.cconvert`](@ref) y pasa las variables directamente al `@ccall`. `@ccall` organiza automáticamente que todos sus argumentos se preserven de la recolección de basura hasta que la llamada regrese. Si una API de C almacenará una referencia a la memoria asignada por Julia, después de que el `@ccall` regrese, debes asegurarte de que el objeto siga siendo visible para el recolector de basura. La forma sugerida de hacer esto es crear una variable global de tipo `Array{Ref,1}` para mantener estos valores hasta que la biblioteca C te notifique que ha terminado con ellos.

Siempre que hayas creado un puntero a datos de Julia, debes asegurarte de que los datos originales existan hasta que hayas terminado de usar el puntero. Muchos métodos en Julia, como [`unsafe_load`](@ref) y [`String`](@ref), hacen copias de los datos en lugar de tomar posesión del búfer, por lo que es seguro liberar (o alterar) los datos originales sin afectar a Julia. Una excepción notable es [`unsafe_wrap`](@ref), que, por razones de rendimiento, comparte (o se le puede indicar que tome posesión de) el búfer subyacente.

El recolector de basura no garantiza ningún orden de finalización. Es decir, si `a` contenía una referencia a `b` y tanto `a` como `b` están listos para la recolección de basura, no hay garantía de que `b` se finalice después de `a`. Si la finalización adecuada de `a` depende de que `b` sea válido, debe manejarse de otras maneras.

## Non-constant Function Specifications

En algunos casos, el nombre o la ruta exacta de la biblioteca necesaria no se conoce de antemano y debe calcularse en tiempo de ejecución. Para manejar tales casos, la especificación del componente de la biblioteca puede ser una llamada a una función, por ejemplo, `find_blas().dgemm`. La expresión de llamada se ejecutará cuando se ejecute el `ccall` en sí. Sin embargo, se asume que la ubicación de la biblioteca no cambia una vez que se determina, por lo que el resultado de la llamada puede ser almacenado en caché y reutilizado. Por lo tanto, el número de veces que se ejecuta la expresión no está especificado, y devolver diferentes valores para múltiples llamadas resulta en un comportamiento no especificado.

Si se necesita aún más flexibilidad, es posible usar valores calculados como nombres de función mediante la etapa a través de [`eval`](@ref) de la siguiente manera:

```julia
@eval @ccall "lib".$(string("a", "b"))()::Cint
```

Esta expresión construye un nombre usando `string`, luego sustituye este nombre en una nueva expresión `@ccall`, que luego se evalúa. Ten en cuenta que `eval` solo opera en el nivel superior, por lo que dentro de esta expresión las variables locales no estarán disponibles (a menos que sus valores sean sustituidos con `$`). Por esta razón, `eval` se utiliza típicamente solo para formar definiciones de nivel superior, por ejemplo, al envolver bibliotecas que contienen muchas funciones similares. Se puede construir un ejemplo similar para [`@cfunction`](@ref).

Sin embargo, hacer esto también será muy lento y filtrará memoria, por lo que generalmente deberías evitarlo y, en su lugar, seguir leyendo. La siguiente sección discute cómo usar llamadas indirectas para lograr de manera eficiente un efecto similar.

## Indirect Calls

El primer argumento de `@ccall` también puede ser una expresión evaluada en tiempo de ejecución. En este caso, la expresión debe evaluarse a un `Ptr`, que se utilizará como la dirección de la función nativa a llamar. Este comportamiento ocurre cuando el primer argumento de `@ccall` contiene referencias a no constantes, como variables locales, argumentos de función o globales no constantes.

Por ejemplo, podrías buscar la función a través de `dlsym`, y luego almacenarla en una referencia compartida para esa sesión. Por ejemplo:

```julia
macro dlsym(lib, func)
    z = Ref{Ptr{Cvoid}}(C_NULL)
    quote
        let zlocal = $z[]
            if zlocal == C_NULL
                zlocal = dlsym($(esc(lib))::Ptr{Cvoid}, $(esc(func)))::Ptr{Cvoid}
                $z[] = zlocal
            end
            zlocal
        end
    end
end

mylibvar = Libdl.dlopen("mylib")
@ccall $(@dlsym(mylibvar, "myfunc"))()::Cvoid
```

## Closure cfunctions

El primer argumento a [`@cfunction`](@ref) puede ser marcado con un `$`, en cuyo caso el valor de retorno será en su lugar un `struct CFunction` que cierra sobre el argumento. Debes asegurarte de que este objeto de retorno se mantenga vivo hasta que se hayan completado todos sus usos. El contenido y el código en el puntero cfunction serán borrados a través de un [`finalizer`](@ref) cuando esta referencia se elimine y atexit. Esto no suele ser necesario, ya que esta funcionalidad no está presente en C, pero puede ser útil para tratar con APIs mal diseñadas que no proporcionan un parámetro de entorno de cierre separado.

```julia
function qsort(a::Vector{T}, cmp) where T
    isbits(T) || throw(ArgumentError("this method can only qsort isbits arrays"))
    callback = @cfunction $cmp Cint (Ref{T}, Ref{T})
    # Here, `callback` isa Base.CFunction, which will be converted to Ptr{Cvoid}
    # (and protected against finalization) by the ccall
    @ccall qsort(a::Ptr{T}, length(a)::Csize_t, Base.elsize(a)::Csize_t, callback::Ptr{Cvoid})
    # We could instead use:
    #    GC.@preserve callback begin
    #        use(Base.unsafe_convert(Ptr{Cvoid}, callback))
    #    end
    # if we needed to use it outside of a `ccall`
    return a
end
```

!!! note
    El cierre [`@cfunction`](@ref) depende de trampolines de LLVM, que no están disponibles en todas las plataformas (por ejemplo, ARM y PowerPC).


## Closing a Library

A veces es útil cerrar (descargar) una biblioteca para que pueda ser recargada. Por ejemplo, al desarrollar código C para usar con Julia, puede ser necesario compilar, llamar al código C desde Julia, luego cerrar la biblioteca, hacer una edición, recompilar y cargar los nuevos cambios. Se puede reiniciar Julia o usar las funciones de `Libdl` para gestionar la biblioteca explícitamente, como:

```julia
lib = Libdl.dlopen("./my_lib.so") # Open the library explicitly.
sym = Libdl.dlsym(lib, :my_fcn)   # Get a symbol for the function to call.
@ccall $sym(...) # Use the pointer `sym` instead of the library.symbol tuple.
Libdl.dlclose(lib) # Close the library explicitly.
```

Tenga en cuenta que al usar `@ccall` con la entrada (por ejemplo, `@ccall "./my_lib.so".my_fcn(...)::Cvoid`), la biblioteca se abre implícitamente y puede que no se cierre explícitamente.

## Variadic function calls

Para llamar a funciones C variádicas, se puede usar un `punto y coma` en la lista de argumentos para separar los argumentos requeridos de los argumentos variádicos. A continuación se muestra un ejemplo con la función `printf`:

```julia-repl
julia> @ccall printf("%s = %d\n"::Cstring ; "foo"::Cstring, foo::Cint)::Cint
foo = 3
8
```

## [`ccall` interface](@id ccall-interface)

Hay otra interfaz alternativa a `@ccall`. Esta interfaz es ligeramente menos conveniente, pero permite especificar un [calling convention](@ref calling-convention).

Los argumentos de [`ccall`](@ref) son:

1. Un par `(:function, "library")` (el más común),

    O bien

    un símbolo de nombre `:function` o una cadena de nombre `"function"` (para símbolos en el proceso actual o libc),

    O bien

    un puntero a función (por ejemplo, de `dlsym`).
2. El tipo de retorno de la función
3. Una tupla de tipos de entrada, correspondiente a la firma de la función. Un error común es olvidar que una tupla de 1 tipo de argumento debe escribirse con una coma al final.
4. Los valores de argumento reales que se pasarán a la función, si los hay; cada uno es un parámetro separado.

!!! note
    El par `(:function, "library")`, el tipo de retorno y los tipos de entrada deben ser constantes literales (es decir, no pueden ser variables, pero vea [Non-constant Function Specifications](@ref)).

    Los parámetros restantes se evalúan en tiempo de compilación, cuando se define el método que los contiene.


A continuación se presenta una tabla de traducciones entre las interfaces de macro y función.

|                                                                     `@ccall` |                                                                     `ccall` |
| ----------------------------------------------------------------------------:| ---------------------------------------------------------------------------:|
|                                                      `@ccall clock()::Int32` |                                                  `ccall(:clock, Int32, ())` |
|                                                    `@ccall f(a::Cint)::Cint` |                                               `ccall(:a, Cint, (Cint,), a)` |
|                               `@ccall "mylib".f(a::Cint, b::Cdouble)::Cvoid` |                      `ccall((:f, "mylib"), Cvoid, (Cint, Cdouble), (a, b))` |
|                                                    `@ccall $fptr.f()::Cvoid` |                                                 `ccall(fptr, f, Cvoid, ())` |
|      `@ccall printf("%s = %d\n"::Cstring ; "foo"::Cstring, foo::Cint)::Cint` |                                                             `<unavailable>` |
| `@ccall printf("%s = %s\n"::Cstring ; "2 + 2"::Cstring, "5"::Cstring)::Cint` |    `ccall(:printf, Cint, (Cstring, Cstring...), "%s = %s\n", "2 + 2", "5")` |
|                                                              `<unavailable>` | `ccall(:gethostname, stdcall, Int32, (Ptr{UInt8}, UInt32), hn, length(hn))` |

## [Calling Convention](@id calling-convention)

El segundo argumento a `ccall` (inmediatamente antes del tipo de retorno) puede ser opcionalmente un especificador de convención de llamada (el macro `@ccall` actualmente no soporta dar una convención de llamada). Sin ningún especificador, se utiliza la convención de llamada C predeterminada de la plataforma. Otras convenciones soportadas son: `stdcall`, `cdecl`, `fastcall` y `thiscall` (sin operación en Windows de 64 bits). Por ejemplo (de `base/libc.jl`) vemos el mismo `gethostname``ccall` que arriba, pero con la firma correcta para Windows:

```julia
hn = Vector{UInt8}(undef, 256)
err = ccall(:gethostname, stdcall, Int32, (Ptr{UInt8}, UInt32), hn, length(hn))
```

Para más información, por favor consulte el [LLVM Language Reference](https://llvm.org/docs/LangRef.html#calling-conventions).

Hay una convención de llamada especial adicional [`llvmcall`](@ref Base.llvmcall), que permite insertar llamadas a intrínsecos de LLVM directamente. Esto puede ser especialmente útil al dirigirse a plataformas inusuales como GPGPUs. Por ejemplo, para [CUDA](https://llvm.org/docs/NVPTXUsage.html), necesitamos poder leer el índice del hilo:

```julia
ccall("llvm.nvvm.read.ptx.sreg.tid.x", llvmcall, Int32, ())
```

Como con cualquier `ccall`, es esencial obtener la firma de los argumentos exactamente correcta. Además, ten en cuenta que no hay una capa de compatibilidad que garantice que el intrínseco tenga sentido y funcione en el objetivo actual, a diferencia de las funciones equivalentes de Julia expuestas por `Core.Intrinsics`.

## Accessing Global Variables

Las variables globales exportadas por bibliotecas nativas se pueden acceder por nombre utilizando la función [`cglobal`](@ref). Los argumentos para `4d61726b646f776e2e436f64652822222c202263676c6f62616c2229_40726566` son una especificación de símbolo idéntica a la utilizada por [`ccall`](@ref), y un tipo que describe el valor almacenado en la variable:

```julia-repl
julia> cglobal((:errno, :libc), Int32)
Ptr{Int32} @0x00007f418d0816b8
```

El resultado es un puntero que da la dirección del valor. El valor se puede manipular a través de este puntero utilizando [`unsafe_load`](@ref) y [`unsafe_store!`](@ref).

!!! note
    Este símbolo `errno` puede no encontrarse en una biblioteca llamada "libc", ya que este es un detalle de implementación de tu compilador del sistema. Típicamente, los símbolos de la biblioteca estándar deberían ser accedidos solo por nombre, permitiendo que el compilador complete el correcto. Sin embargo, el símbolo `errno` mostrado en este ejemplo es especial en la mayoría de los compiladores, por lo que el valor visto aquí probablemente no sea lo que esperas o deseas. Compilar el código equivalente en C en cualquier sistema capaz de multi-hilo típicamente llamaría a una función diferente (a través de la sobrecarga del preprocesador de macros), y puede dar un resultado diferente al valor legado impreso aquí.


## Accessing Data through a Pointer

Los siguientes métodos se describen como "inseguros" porque un puntero o declaración de tipo incorrectos pueden hacer que Julia termine abruptamente.

Dado un `Ptr{T}`, el contenido del tipo `T` se puede copiar generalmente de la memoria referenciada a un objeto de Julia utilizando `unsafe_load(ptr, [índice])`. El argumento índice es opcional (el valor predeterminado es 1) y sigue la convención de Julia de indexación basada en 1. Esta función es intencionalmente similar al comportamiento de [`getindex`](@ref) y [`setindex!`](@ref) (por ejemplo, la sintaxis de acceso `[]`).

El valor de retorno será un nuevo objeto inicializado para contener una copia del contenido de la memoria referenciada. La memoria referenciada se puede liberar o soltar de manera segura.

Si `T` es `Any`, entonces se asume que la memoria contiene una referencia a un objeto de Julia (un `jl_value_t*`), el resultado será una referencia a este objeto, y el objeto no será copiado. Debes tener cuidado en este caso para asegurarte de que el objeto siempre fue visible para el recolector de basura (los punteros no cuentan, pero la nueva referencia sí) para garantizar que la memoria no se libere prematuramente. Ten en cuenta que si el objeto no fue originalmente asignado por Julia, el nuevo objeto nunca será finalizado por el recolector de basura de Julia. Si el `Ptr` en sí es en realidad un `jl_value_t*`, se puede convertir de nuevo a una referencia de objeto de Julia mediante [`unsafe_pointer_to_objref(ptr)`](@ref). (Los valores de Julia `v` se pueden convertir a punteros `jl_value_t*`, como `Ptr{Cvoid}`, llamando a [`pointer_from_objref(v)`](@ref).)

La operación inversa (escribir datos en un `Ptr{T}`) se puede realizar utilizando [`unsafe_store!(ptr, value, [index])`](@ref). Actualmente, esto solo es compatible con tipos primitivos u otros tipos de estructuras inmutables sin punteros (`isbits`).

Cualquier operación que genere un error probablemente no esté implementada actualmente y debería ser publicada como un error para que pueda ser resuelto.

Si el puntero de interés es un arreglo de datos simples (tipo primitivo o estructura inmutable), la función [`unsafe_wrap(Array, ptr,dims, own = false)`](@ref) puede ser más útil. El parámetro final debe ser verdadero si Julia debe "tomar posesión" del búfer subyacente y llamar a `free(ptr)` cuando el objeto `Array` devuelto se finalice. Si el parámetro `own` se omite o es falso, el llamador debe asegurarse de que el búfer permanezca en existencia hasta que se complete todo el acceso.

La aritmética en el tipo `Ptr` en Julia (por ejemplo, usando `+`) no se comporta de la misma manera que la aritmética de punteros en C. Al sumar un entero a un `Ptr` en Julia, el puntero siempre se mueve por un número de *bytes*, no de elementos. De esta manera, los valores de dirección obtenidos de la aritmética de punteros no dependen de los tipos de elementos de los punteros.

## Thread-safety

Algunas bibliotecas de C ejecutan sus callbacks desde un hilo diferente, y dado que Julia no es segura para hilos, necesitarás tomar algunas precauciones adicionales. En particular, necesitarás configurar un sistema de dos capas: el callback de C solo debe *programar* (a través del bucle de eventos de Julia) la ejecución de tu callback "real". Para hacer esto, crea un [`AsyncCondition`](@ref Base.AsyncCondition) objeto y [`wait`](@ref) sobre él:

```julia
cond = Base.AsyncCondition()
wait(cond)
```

El callback que pases a C solo debe ejecutar un [`ccall`](@ref) a `:uv_async_send`, pasando `cond.handle` como argumento, cuidando de evitar cualquier asignación o interacción con el tiempo de ejecución de Julia.

Tenga en cuenta que los eventos pueden ser fusionados, por lo que múltiples llamadas a `uv_async_send` pueden resultar en una única notificación de activación a la condición.

## More About Callbacks

Para más detalles sobre cómo pasar callbacks a bibliotecas C, consulta este [blog post](https://julialang.org/blog/2013/05/callback).

## C++

Para herramientas para crear enlaces de C++, consulta el paquete [CxxWrap](https://github.com/JuliaInterop/CxxWrap.jl).

[^1]: Non-library function calls in both C and Julia can be inlined and thus may have even less overhead than calls to shared library functions. The point above is that the cost of actually doing foreign function call is about the same as doing a call in either native language.

[^2]: The [Clang package](https://github.com/ihnorton/Clang.jl) can be used to auto-generate Julia code from a C header file.
