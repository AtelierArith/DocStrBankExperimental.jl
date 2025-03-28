# Methods

Recuerda de [Functions](@ref man-functions) que una función es un objeto que mapea una tupla de argumentos a un valor de retorno, o lanza una excepción si no se puede devolver un valor apropiado. Es común que la misma función o operación conceptual se implemente de manera bastante diferente para diferentes tipos de argumentos: sumar dos enteros es muy diferente de sumar dos números de punto flotante, ambos de los cuales son distintos de sumar un entero a un número de punto flotante. A pesar de sus diferencias de implementación, todas estas operaciones caen bajo el concepto general de "suma". En consecuencia, en Julia, estos comportamientos pertenecen a un solo objeto: la función `+`.

Para facilitar el uso de muchas implementaciones diferentes del mismo concepto de manera fluida, las funciones no necesitan definirse todas de una vez, sino que pueden definirse por partes al proporcionar comportamientos específicos para ciertas combinaciones de tipos y cantidades de argumentos. Una definición de un posible comportamiento para una función se llama *método*. Hasta ahora, solo hemos presentado ejemplos de funciones definidas con un solo método, aplicable a todos los tipos de argumentos. Sin embargo, las firmas de las definiciones de métodos pueden ser anotadas para indicar los tipos de argumentos además de su número, y se puede proporcionar más de una definición de método. Cuando una función se aplica a una tupla particular de argumentos, se aplica el método más específico aplicable a esos argumentos. Así, el comportamiento general de una función es un patchwork de los comportamientos de sus diversas definiciones de método. Si el patchwork está bien diseñado, aunque las implementaciones de los métodos pueden ser bastante diferentes, el comportamiento externo de la función parecerá fluido y consistente.

La elección de qué método ejecutar cuando se aplica una función se llama *despacho*. Julia permite que el proceso de despacho elija cuál de los métodos de una función llamar en función del número de argumentos dados y de los tipos de todos los argumentos de la función. Esto es diferente de los lenguajes de programación orientados a objetos tradicionales, donde el despacho ocurre solo en función del primer argumento, que a menudo tiene una sintaxis de argumento especial y a veces se implica en lugar de escribirse explícitamente como un argumento. [^1] Usar todos los argumentos de una función para elegir qué método debe ser invocado, en lugar de solo el primero, se conoce como [multiple dispatch](https://en.wikipedia.org/wiki/Multiple_dispatch). El despacho múltiple es particularmente útil para el código matemático, donde tiene poco sentido considerar artificialmente que las operaciones "pertenecen" a un argumento más que a los otros: ¿pertenece la operación de suma en `x + y` a `x` más que a `y`? La implementación de un operador matemático generalmente depende de los tipos de todos sus argumentos. Sin embargo, incluso más allá de las operaciones matemáticas, el despacho múltiple resulta ser un paradigma poderoso y conveniente para estructurar y organizar programas.

[^1]: In C++ or Java, for example, in a method call like `obj.meth(arg1,arg2)`, the object obj "receives" the method call and is implicitly passed to the method via the `this` keyword, rather than as an explicit method argument. When the current `this` object is the receiver of a method call, it can be omitted altogether, writing just `meth(arg1,arg2)`, with `this` implied as the receiving object.

!!! note
    Todos los ejemplos en este capítulo asumen que estás definiendo métodos para una función en el *mismo* módulo. Si deseas agregar métodos a una función en *otro* módulo, debes `importarlo` o usar el nombre calificado con los nombres de los módulos. Consulta la sección sobre [namespace management](@ref namespace-management).


## Defining Methods

Hasta ahora, en nuestros ejemplos, solo hemos definido funciones con un único método que tiene tipos de argumento no restringidos. Tales funciones se comportan exactamente como lo harían en lenguajes dinámicamente tipados tradicionales. Sin embargo, hemos utilizado el despacho múltiple y métodos casi continuamente sin ser conscientes de ello: todas las funciones y operadores estándar de Julia, como la función `+` mencionada anteriormente, tienen muchos métodos que definen su comportamiento sobre varias combinaciones posibles de tipo y cantidad de argumentos.

Al definir una función, se puede opcionalmente restringir los tipos de parámetros a los que es aplicable, utilizando el operador de aserción de tipo `::`, introducido en la sección sobre [Composite Types](@ref):

```jldoctest fofxy
julia> f(x::Float64, y::Float64) = 2x + y
f (generic function with 1 method)
```

Esta definición de función se aplica solo a llamadas donde `x` e `y` son ambos valores del tipo [`Float64`](@ref):

```jldoctest fofxy
julia> f(2.0, 3.0)
7.0
```

Aplicarlo a cualquier otro tipo de argumentos resultará en un [`MethodError`](@ref):

```jldoctest fofxy
julia> f(2.0, 3)
ERROR: MethodError: no method matching f(::Float64, ::Int64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f(Float32(2.0), 3.0)
ERROR: MethodError: no method matching f(::Float32, ::Float64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Float64, ::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f(2.0, "3.0")
ERROR: MethodError: no method matching f(::Float64, ::String)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f("2.0", "3.0")
ERROR: MethodError: no method matching f(::String, ::String)
The function `f` exists, but no method is defined for this combination of argument types.
```

Como puedes ver, los argumentos deben ser precisamente del tipo [`Float64`](@ref). Otros tipos numéricos, como enteros o valores de punto flotante de 32 bits, no se convierten automáticamente a punto flotante de 64 bits, ni se analizan las cadenas como números. Debido a que `Float64` es un tipo concreto y los tipos concretos no pueden ser subclase en Julia, tal definición solo se puede aplicar a argumentos que son exactamente del tipo `Float64`. Sin embargo, a menudo puede ser útil escribir métodos más generales donde los tipos de parámetros declarados son abstractos:

```jldoctest fofxy
julia> f(x::Number, y::Number) = 2x - y
f (generic function with 2 methods)

julia> f(2.0, 3)
1.0
```

Esta definición de método se aplica a cualquier par de argumentos que sean instancias de [`Number`](@ref). No es necesario que sean del mismo tipo, siempre que cada uno de ellos sea un valor numérico. El problema de manejar tipos numéricos dispares se delega a las operaciones aritméticas en la expresión `2x - y`.

Para definir una función con múltiples métodos, simplemente se define la función varias veces, con diferentes números y tipos de argumentos. La primera definición del método para una función crea el objeto de función, y las definiciones de métodos subsiguientes añaden nuevos métodos al objeto de función existente. La definición de método más específica que coincida con el número y tipos de los argumentos se ejecutará cuando se aplique la función. Así, las dos definiciones de método anteriores, tomadas en conjunto, definen el comportamiento de `f` sobre todos los pares de instancias del tipo abstracto `Number` – pero con un comportamiento diferente específico para pares de valores [`Float64`](@ref). Si uno de los argumentos es un float de 64 bits pero el otro no lo es, entonces el método `f(Float64,Float64)` no puede ser llamado y debe usarse el método más general `f(Number,Number)`:

```jldoctest fofxy
julia> f(2.0, 3.0)
7.0

julia> f(2, 3.0)
1.0

julia> f(2.0, 3)
1.0

julia> f(2, 3)
1
```

The `2x + y` definition is only used in the first case, while the `2x - y` definition is used in the others. No automatic casting or conversion of function arguments is ever performed: all conversion in Julia is non-magical and completely explicit. [Conversion and Promotion](@ref conversion-and-promotion), however, shows how clever application of sufficiently advanced technology can be indistinguishable from magic. [^Clarke61]

For non-numeric values, and for fewer or more than two arguments, the function `f` remains undefined, and applying it will still result in a [`MethodError`](@ref):

```jldoctest fofxy
julia> f("foo", 3)
ERROR: MethodError: no method matching f(::String, ::Int64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Number, ::Number)
   @ Main none:1
  f(!Matched::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f()
ERROR: MethodError: no method matching f()
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Float64, !Matched::Float64)
   @ Main none:1
  f(!Matched::Number, !Matched::Number)
   @ Main none:1

Stacktrace:
[...]
```

Puedes ver fácilmente qué métodos existen para una función ingresando el objeto de la función en una sesión interactiva:

```jldoctest fofxy
julia> f
f (generic function with 2 methods)
```

Esta salida nos dice que `f` es un objeto de función con dos métodos. Para averiguar cuáles son las firmas de esos métodos, utiliza la función [`methods`](@ref):

```jldoctest fofxy
julia> methods(f)
# 2 methods for generic function "f" from Main:
 [1] f(x::Float64, y::Float64)
     @ none:1
 [2] f(x::Number, y::Number)
     @ none:1
```

lo que muestra que `f` tiene dos métodos, uno que toma dos argumentos `Float64` y otro que toma argumentos de tipo `Number`. También indica el archivo y el número de línea donde se definieron los métodos: dado que estos métodos se definieron en el REPL, obtenemos el número de línea aparente `none:1`.

En ausencia de una declaración de tipo con `::`, el tipo de un parámetro de método es `Any` por defecto, lo que significa que no está restringido, ya que todos los valores en Julia son instancias del tipo abstracto `Any`. Por lo tanto, podemos definir un método que capture todo para `f` de la siguiente manera:

```jldoctest fofxy
julia> f(x,y) = println("Whoa there, Nelly.")
f (generic function with 3 methods)

julia> methods(f)
# 3 methods for generic function "f" from Main:
 [1] f(x::Float64, y::Float64)
     @ none:1
 [2] f(x::Number, y::Number)
     @ none:1
 [3] f(x, y)
     @ none:1

julia> f("foo", 1)
Whoa there, Nelly.
```

Este catch-all es menos específico que cualquier otra posible definición de método para un par de valores de parámetro, por lo que solo se llamará en pares de argumentos a los que no se aplique ninguna otra definición de método.

Tenga en cuenta que en la firma del tercer método, no se especifica un tipo para los argumentos `x` e `y`. Esta es una forma abreviada de expresar `f(x::Any, y::Any)`.

Aunque parece un concepto simple, el despacho múltiple basado en los tipos de valores es quizás la característica más poderosa y central del lenguaje Julia. Las operaciones básicas suelen tener docenas de métodos:

```julia-repl
julia> methods(+)
# 180 methods for generic function "+":
[1] +(x::Bool, z::Complex{Bool}) in Base at complex.jl:227
[2] +(x::Bool, y::Bool) in Base at bool.jl:89
[3] +(x::Bool) in Base at bool.jl:86
[4] +(x::Bool, y::T) where T<:AbstractFloat in Base at bool.jl:96
[5] +(x::Bool, z::Complex) in Base at complex.jl:234
[6] +(a::Float16, b::Float16) in Base at float.jl:373
[7] +(x::Float32, y::Float32) in Base at float.jl:375
[8] +(x::Float64, y::Float64) in Base at float.jl:376
[9] +(z::Complex{Bool}, x::Bool) in Base at complex.jl:228
[10] +(z::Complex{Bool}, x::Real) in Base at complex.jl:242
[11] +(x::Char, y::Integer) in Base at char.jl:40
[12] +(c::BigInt, x::BigFloat) in Base.MPFR at mpfr.jl:307
[13] +(a::BigInt, b::BigInt, c::BigInt, d::BigInt, e::BigInt) in Base.GMP at gmp.jl:392
[14] +(a::BigInt, b::BigInt, c::BigInt, d::BigInt) in Base.GMP at gmp.jl:391
[15] +(a::BigInt, b::BigInt, c::BigInt) in Base.GMP at gmp.jl:390
[16] +(x::BigInt, y::BigInt) in Base.GMP at gmp.jl:361
[17] +(x::BigInt, c::Union{UInt16, UInt32, UInt64, UInt8}) in Base.GMP at gmp.jl:398
...
[180] +(a, b, c, xs...) in Base at operators.jl:424
```

El despacho múltiple junto con el sistema de tipos paramétricos flexible le da a Julia su capacidad para expresar de manera abstracta algoritmos de alto nivel desacoplados de los detalles de implementación.

## [Method specializations](@id man-method-specializations)

Cuando creas múltiples métodos de la misma función, a veces se llama "especialización". En este caso, estás especializando la *función* al agregarle métodos adicionales: cada nuevo método es una nueva especialización de la función. Como se mostró arriba, estas especializaciones son devueltas por `methods`.

Hay otro tipo de especialización que ocurre sin intervención del programador: el compilador de Julia puede especializar automáticamente el *método* para los tipos de argumento específicos utilizados. Tales especializaciones *no* se enumeran con `methods`, ya que esto no crea nuevos `Method`s, pero herramientas como [`@code_typed`](@ref) te permiten inspeccionar tales especializaciones.

Por ejemplo, si creas un método

```
mysum(x::Real, y::Real) = x + y
```

has dado a la función `mysum` un nuevo método (posiblemente su único método), y ese método toma cualquier par de entradas de números `Real`. Pero si luego ejecutas

```julia-repl
julia> mysum(1, 2)
3

julia> mysum(1.0, 2.0)
3.0
```

Julia compilará `mysum` dos veces, una para `x::Int, y::Int` y otra vez para `x::Float64, y::Float64`. El objetivo de compilar dos veces es el rendimiento: los métodos que se llaman para `+` (que `mysum` utiliza) varían dependiendo de los tipos específicos de `x` y `y`, y al compilar diferentes especializaciones, Julia puede hacer toda la búsqueda de métodos por adelantado. Esto permite que el programa se ejecute mucho más rápido, ya que no tiene que preocuparse por la búsqueda de métodos mientras se está ejecutando. La especialización automática de Julia te permite escribir algoritmos genéricos y esperar que el compilador genere código eficiente y especializado para manejar cada caso que necesites.

En casos donde el número de especializaciones potenciales podría ser efectivamente ilimitado, Julia puede evitar esta especialización predeterminada. Consulta [Be aware of when Julia avoids specializing](@ref) para más información.

## [Method Ambiguities](@id man-ambiguities)

Es posible definir un conjunto de métodos de función de tal manera que no haya un método más específico único aplicable a algunas combinaciones de argumentos:

```jldoctest gofxy
julia> g(x::Float64, y) = 2x + y
g (generic function with 1 method)

julia> g(x, y::Float64) = x + 2y
g (generic function with 2 methods)

julia> g(2.0, 3)
7.0

julia> g(2, 3.0)
8.0

julia> g(2.0, 3.0)
ERROR: MethodError: g(::Float64, ::Float64) is ambiguous.

Candidates:
  g(x, y::Float64)
    @ Main none:1
  g(x::Float64, y)
    @ Main none:1

Possible fix, define
  g(::Float64, ::Float64)

Stacktrace:
[...]
```

Aquí la llamada `g(2.0, 3.0)` podría ser manejada por el método `g(::Float64, ::Any)` o el método `g(::Any, ::Float64)`. El orden en que se definen los métodos no importa y ninguno es más específico que el otro. En tales casos, Julia genera un [`MethodError`](@ref) en lugar de elegir arbitrariamente un método. Puedes evitar ambigüedades de método especificando un método apropiado para el caso de intersección:

```jldoctest gofxy
julia> g(x::Float64, y::Float64) = 2x + 2y
g (generic function with 3 methods)

julia> g(2.0, 3)
7.0

julia> g(2, 3.0)
8.0

julia> g(2.0, 3.0)
10.0
```

Se recomienda que el método de desambiguación se defina primero, ya que de lo contrario existe ambigüedad, aunque sea de forma transitoria, hasta que se defina el método más específico.

En casos más complejos, resolver ambigüedades de métodos implica un cierto elemento de diseño; este tema se explora más a fondo [below](@ref man-method-design-ambiguities).

## Parametric Methods

Las definiciones de métodos pueden tener opcionalmente parámetros de tipo que califican la firma:

```jldoctest same_typefunc
julia> same_type(x::T, y::T) where {T} = true
same_type (generic function with 1 method)

julia> same_type(x,y) = false
same_type (generic function with 2 methods)
```

El primer método se aplica siempre que ambos argumentos sean del mismo tipo concreto, sin importar cuál sea ese tipo, mientras que el segundo método actúa como un catch-all, cubriendo todos los demás casos. Así, en general, esto define una función booleana que verifica si sus dos argumentos son del mismo tipo:

```jldoctest same_typefunc
julia> same_type(1, 2)
true

julia> same_type(1, 2.0)
false

julia> same_type(1.0, 2.0)
true

julia> same_type("foo", 2.0)
false

julia> same_type("foo", "bar")
true

julia> same_type(Int32(1), Int64(2))
false
```

Tales definiciones corresponden a métodos cuyas firmas de tipo son tipos `UnionAll` (ver [UnionAll Types](@ref)).

Este tipo de definición del comportamiento de la función por despacho es bastante común – incluso idiomática – en Julia. Los parámetros de tipo de método no están restringidos a ser utilizados como los tipos de argumentos: pueden ser utilizados en cualquier lugar donde un valor estaría en la firma de la función o en el cuerpo de la función. Aquí hay un ejemplo donde el parámetro de tipo de método `T` se utiliza como el parámetro de tipo para el tipo paramétrico `Vector{T}` en la firma del método:

```jldoctest
julia> function myappend(v::Vector{T}, x::T) where {T}
           return [v..., x]
       end
myappend (generic function with 1 method)
```

El parámetro de tipo `T` en este ejemplo asegura que el elemento añadido `x` sea un subtipo del tipo existente de los elementos del vector `v`. La palabra clave `where` introduce una lista de esas restricciones después de la definición de la firma del método. Esto funciona de la misma manera para definiciones de una línea, como se vio arriba, y debe aparecer *antes* de [return type declaration](@ref man-functions-return-type), si está presente, como se ilustra a continuación:

```jldoctest
julia> (myappend(v::Vector{T}, x::T)::Vector) where {T} = [v..., x]
myappend (generic function with 1 method)

julia> myappend([1,2,3],4)
4-element Vector{Int64}:
 1
 2
 3
 4

julia> myappend([1,2,3],2.5)
ERROR: MethodError: no method matching myappend(::Vector{Int64}, ::Float64)
The function `myappend` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  myappend(::Vector{T}, !Matched::T) where T
   @ Main none:1

Stacktrace:
[...]

julia> myappend([1.0,2.0,3.0],4.0)
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0

julia> myappend([1.0,2.0,3.0],4)
ERROR: MethodError: no method matching myappend(::Vector{Float64}, ::Int64)
The function `myappend` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  myappend(::Vector{T}, !Matched::T) where T
   @ Main none:1

Stacktrace:
[...]
```

Si el tipo del elemento agregado no coincide con el tipo de elemento del vector al que se agrega, se genera un [`MethodError`](@ref). En el siguiente ejemplo, el parámetro de tipo del método `T` se utiliza como valor de retorno:

```jldoctest
julia> mytypeof(x::T) where {T} = T
mytypeof (generic function with 1 method)

julia> mytypeof(1)
Int64

julia> mytypeof(1.0)
Float64
```

Así como puedes poner restricciones de subtipo en los parámetros de tipo en las declaraciones de tipo (ver [Parametric Types](@ref)), también puedes restringir los parámetros de tipo de los métodos:

```jldoctest
julia> same_type_numeric(x::T, y::T) where {T<:Number} = true
same_type_numeric (generic function with 1 method)

julia> same_type_numeric(x::Number, y::Number) = false
same_type_numeric (generic function with 2 methods)

julia> same_type_numeric(1, 2)
true

julia> same_type_numeric(1, 2.0)
false

julia> same_type_numeric(1.0, 2.0)
true

julia> same_type_numeric("foo", 2.0)
ERROR: MethodError: no method matching same_type_numeric(::String, ::Float64)
The function `same_type_numeric` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  same_type_numeric(!Matched::T, ::T) where T<:Number
   @ Main none:1
  same_type_numeric(!Matched::Number, ::Number)
   @ Main none:1

Stacktrace:
[...]

julia> same_type_numeric("foo", "bar")
ERROR: MethodError: no method matching same_type_numeric(::String, ::String)
The function `same_type_numeric` exists, but no method is defined for this combination of argument types.

julia> same_type_numeric(Int32(1), Int64(2))
false
```

La función `same_type_numeric` se comporta de manera similar a la función `same_type` definida anteriormente, pero solo está definida para pares de números.

Los métodos paramétricos permiten la misma sintaxis que las expresiones `where` utilizadas para escribir tipos (ver [UnionAll Types](@ref)). Si hay solo un parámetro, las llaves de cierre (en `where {T}`) se pueden omitir, pero a menudo se prefieren por claridad. Múltiples parámetros se pueden separar con comas, por ejemplo, `where {T, S<:Real}`, o escribirse utilizando `where` anidados, por ejemplo, `where S<:Real where T`.

## Redefining Methods

Al redefinir un método o agregar nuevos métodos, es importante darse cuenta de que estos cambios no tienen efecto inmediato. Esto es clave para la capacidad de Julia de inferir y compilar código de manera estática para ejecutarse rápidamente, sin los trucos y sobrecargas habituales de JIT. De hecho, cualquier nueva definición de método no será visible para el entorno de ejecución actual, incluidos Tareas e Hilos (y cualquier función `@generated` definida previamente). Comencemos con un ejemplo para ver qué significa esto:

```julia-repl
julia> function tryeval()
           @eval newfun() = 1
           newfun()
       end
tryeval (generic function with 1 method)

julia> tryeval()
ERROR: MethodError: no method matching newfun()
The applicable method may be too new: running in world age xxxx1, while current world is xxxx2.
Closest candidates are:
  newfun() at none:1 (method too new to be called from this world context.)
 in tryeval() at none:1
 ...

julia> newfun()
1
```

En este ejemplo, observa que se ha creado una nueva definición para `newfun`, pero no se puede llamar de inmediato. El nuevo global es inmediatamente visible para la función `tryeval`, por lo que podrías escribir `return newfun` (sin paréntesis). Pero ni tú, ni ninguno de tus llamadores, ni las funciones que ellos llaman, etc., pueden llamar a esta nueva definición de método.

Pero hay una excepción: las llamadas futuras a `newfun` *desde el REPL* funcionan como se espera, pudiendo ver y llamar a la nueva definición de `newfun`.

Sin embargo, las llamadas futuras a `tryeval` seguirán viendo la definición de `newfun` tal como estaba *en la declaración anterior en el REPL*, y por lo tanto antes de esa llamada a `tryeval`.

Puede que quieras probar esto por ti mismo para ver cómo funciona.

La implementación de este comportamiento es un "contador de edad del mundo". Este valor que aumenta monotonamente rastrea cada operación de definición de método. Esto permite describir "el conjunto de definiciones de métodos visibles para un entorno de ejecución dado" como un solo número, o "edad del mundo". También permite comparar los métodos disponibles en dos mundos simplemente comparando su valor ordinal. En el ejemplo anterior, vemos que el "mundo actual" (en el que existe el método `newfun`), es uno mayor que el "mundo de ejecución" local de la tarea que se fijó cuando comenzó la ejecución de `tryeval`.

A veces es necesario sortear esto (por ejemplo, si estás implementando el REPL anterior). Afortunadamente, hay una solución fácil: llama a la función usando [`Base.invokelatest`](@ref):

```jldoctest
julia> function tryeval2()
           @eval newfun2() = 2
           Base.invokelatest(newfun2)
       end
tryeval2 (generic function with 1 method)

julia> tryeval2()
2
```

Finalmente, echemos un vistazo a algunos ejemplos más complejos donde esta regla entra en juego. Define una función `f(x)`, que inicialmente tiene un método:

```jldoctest redefinemethod
julia> f(x) = "original definition"
f (generic function with 1 method)
```

Iniciar algunas otras operaciones que utilizan `f(x)`:

```jldoctest redefinemethod
julia> g(x) = f(x)
g (generic function with 1 method)

julia> t = @async f(wait()); yield();
```

Ahora añadimos algunos nuevos métodos a `f(x)`:`

```jldoctest redefinemethod
julia> f(x::Int) = "definition for Int"
f (generic function with 2 methods)

julia> f(x::Type{Int}) = "definition for Type{Int}"
f (generic function with 3 methods)
```

Compara cómo difieren estos resultados:

```jldoctest redefinemethod
julia> f(1)
"definition for Int"

julia> g(1)
"definition for Int"

julia> fetch(schedule(t, 1))
"original definition"

julia> t = @async f(wait()); yield();

julia> fetch(schedule(t, 1))
"definition for Int"
```

## Design Patterns with Parametric Methods

Aunque la lógica de despacho compleja no es necesaria para el rendimiento o la usabilidad, a veces puede ser la mejor manera de expresar algún algoritmo. Aquí hay algunos patrones de diseño comunes que a veces surgen al usar el despacho de esta manera.

### Extracting the type parameter from a super-type

Aquí hay una plantilla de código correcta para devolver el tipo de elemento `T` de cualquier subtipo arbitrario de `AbstractArray` que tenga un tipo de elemento bien definido:

```julia
abstract type AbstractArray{T, N} end
eltype(::Type{<:AbstractArray{T}}) where {T} = T
```

usando el llamado despacho triangular. Tenga en cuenta que los tipos `UnionAll`, por ejemplo `eltype(AbstractArray{T} where T <: Integer)`, no coinciden con el método anterior. La implementación de `eltype` en `Base` agrega un método de respaldo a `Any` para tales casos.

Un error común es intentar obtener el tipo de elemento utilizando introspección:

```julia
eltype_wrong(::Type{A}) where {A<:AbstractArray} = A.parameters[1]
```

Sin embargo, no es difícil construir casos en los que esto fallará:

```julia
struct BitVector <: AbstractArray{Bool, 1}; end
```

Aquí hemos creado un tipo `BitVector` que no tiene parámetros, pero donde el tipo de elemento está completamente especificado, ¡con `T` igual a `Bool`!

Otro error es intentar recorrer la jerarquía de tipos utilizando `supertype`:

```julia
eltype_wrong(::Type{AbstractArray{T}}) where {T} = T
eltype_wrong(::Type{AbstractArray{T, N}}) where {T, N} = T
eltype_wrong(::Type{A}) where {A<:AbstractArray} = eltype_wrong(supertype(A))
```

Mientras esto funciona para tipos declarados, falla para tipos sin supertipos:

```julia-repl
julia> eltype_wrong(Union{AbstractArray{Int}, AbstractArray{Float64}})
ERROR: MethodError: no method matching supertype(::Type{Union{AbstractArray{Float64,N} where N, AbstractArray{Int64,N} where N}})
Closest candidates are:
  supertype(::DataType) at operators.jl:43
  supertype(::UnionAll) at operators.jl:48
```

### Building a similar type with a different type parameter

Al construir código genérico, a menudo hay una necesidad de construir un objeto similar con algún cambio en el diseño del tipo, lo que también requiere un cambio en los parámetros de tipo. Por ejemplo, podrías tener algún tipo de arreglo abstracto con un tipo de elemento arbitrario y querer escribir tu computación sobre él con un tipo de elemento específico. Debemos implementar un método para cada subtipo de `AbstractArray{T}` que describa cómo computar esta transformación de tipo. No hay una transformación general de un subtipo a otro subtipo con un parámetro diferente.

Los subtipos de `AbstractArray` típicamente implementan dos métodos para lograr esto: un método para convertir el array de entrada a un subtipo de un tipo abstracto específico `AbstractArray{T, N}`; y un método para crear un nuevo array no inicializado con un tipo de elemento específico. Se pueden encontrar implementaciones de muestra de estos en Julia Base. Aquí hay un ejemplo básico de uso de ellos, garantizando que `input` y `output` sean del mismo tipo:

```julia
input = convert(AbstractArray{Eltype}, input)
output = similar(input, Eltype)
```

Como extensión de esto, en casos donde el algoritmo necesita una copia del array de entrada, [`convert`](@ref) es insuficiente ya que el valor de retorno puede aliasar la entrada original. Combinar [`similar`](@ref) (para hacer el array de salida) y [`copyto!`](@ref) (para llenarlo con los datos de entrada) es una forma genérica de expresar el requisito de una copia mutable del argumento de entrada:

```julia
copy_with_eltype(input, Eltype) = copyto!(similar(input, Eltype), input)
```

### Iterated dispatch

Para despachar una lista de argumentos paramétricos de múltiples niveles, a menudo es mejor separar cada nivel de despacho en funciones distintas. Esto puede sonar similar en enfoque al despacho único, pero como veremos a continuación, sigue siendo más flexible.

Por ejemplo, intentar despachar en el tipo de elemento de un arreglo a menudo se encontrará con situaciones ambiguas. En su lugar, comúnmente el código despachará primero en el tipo de contenedor, luego recursará hacia un método más específico basado en el tipo de elemento. En la mayoría de los casos, los algoritmos se prestan convenientemente a este enfoque jerárquico, mientras que en otros casos, este rigor debe resolverse manualmente. Este ramificación de despachos se puede observar, por ejemplo, en la lógica para sumar dos matrices:

```julia
# First dispatch selects the map algorithm for element-wise summation.
+(a::Matrix, b::Matrix) = map(+, a, b)
# Then dispatch handles each element and selects the appropriate
# common element type for the computation.
+(a, b) = +(promote(a, b)...)
# Once the elements have the same type, they can be added.
# For example, via primitive operations exposed by the processor.
+(a::Float64, b::Float64) = Core.add(a, b)
```

### Trait-based dispatch

Una extensión natural al despacho iterado anterior es agregar una capa a la selección de métodos que permita despachar sobre conjuntos de tipos que son independientes de los conjuntos definidos por la jerarquía de tipos. Podríamos construir tal conjunto escribiendo una `Unión` de los tipos en cuestión, pero entonces este conjunto no sería extensible ya que los tipos `Unión` no pueden ser alterados después de su creación. Sin embargo, tal conjunto extensible se puede programar con un patrón de diseño a menudo referido como un ["Holy-trait"](https://github.com/JuliaLang/julia/issues/2345#issuecomment-54537633).

Este patrón se implementa definiendo una función genérica que calcula un valor (o tipo) singleton diferente para cada conjunto de rasgos al que pueden pertenecer los argumentos de la función. Si esta función es pura, no hay impacto en el rendimiento en comparación con el despacho normal.

El ejemplo en la sección anterior pasó por alto los detalles de implementación de [`map`](@ref) y [`promote`](@ref), que operan en términos de estos rasgos. Al iterar sobre una matriz, como en la implementación de `map`, una pregunta importante es qué orden usar para recorrer los datos. Cuando los subtipos de `AbstractArray` implementan el rasgo [`Base.IndexStyle`](@ref), otras funciones como `map` pueden despachar esta información para elegir el mejor algoritmo (ver [Abstract Array Interface](@ref man-interface-array)). Esto significa que cada subtipo no necesita implementar una versión personalizada de `map`, ya que las definiciones genéricas + clases de rasgos permitirán al sistema seleccionar la versión más rápida. Aquí hay una implementación de juguete de `map` que ilustra el despacho basado en rasgos:

```julia
map(f, a::AbstractArray, b::AbstractArray) = map(Base.IndexStyle(a, b), f, a, b)
# generic implementation:
map(::Base.IndexCartesian, f, a::AbstractArray, b::AbstractArray) = ...
# linear-indexing implementation (faster)
map(::Base.IndexLinear, f, a::AbstractArray, b::AbstractArray) = ...
```

Este enfoque basado en rasgos también está presente en el mecanismo [`promote`](@ref) empleado por el escalar `+`. Utiliza [`promote_type`](@ref), que devuelve el tipo común óptimo para calcular la operación dada los dos tipos de los operandos. Esto hace posible reducir el problema de implementar cada función para cada par de posibles argumentos de tipo, al problema mucho más pequeño de implementar una operación de conversión de cada tipo a un tipo común, más una tabla de reglas de promoción preferidas por pares.

### Output-type computation

La discusión sobre la promoción basada en rasgos proporciona una transición a nuestro siguiente patrón de diseño: calcular el tipo de elemento de salida para una operación de matriz.

Para implementar operaciones primitivas, como la adición, utilizamos la función [`promote_type`](@ref) para calcular el tipo de salida deseado. (Como antes, vimos esto en acción en la llamada a `promote` en la llamada a `+`).

Para funciones más complejas sobre matrices, puede ser necesario calcular el tipo de retorno esperado para una secuencia más compleja de operaciones. Esto se realiza a menudo mediante los siguientes pasos:

1. Write a small function `op` that expresses the set of operations performed by the kernel of the algorithm.
2. Calcule el tipo de elemento `R` de la matriz resultante como `promote_op(op, argument_types...)`, donde `argument_types` se calcula a partir de `eltype` aplicado a cada matriz de entrada.
3. Construya la matriz de salida como `similar(R, dims)`, donde `dims` son las dimensiones deseadas de la matriz de salida.

Para un ejemplo más específico, un pseudo-código genérico para la multiplicación de matrices cuadradas podría verse así:

```julia
function matmul(a::AbstractMatrix, b::AbstractMatrix)
    op = (ai, bi) -> ai * bi + ai * bi

    ## this is insufficient because it assumes `one(eltype(a))` is constructable:
    # R = typeof(op(one(eltype(a)), one(eltype(b))))

    ## this fails because it assumes `a[1]` exists and is representative of all elements of the array
    # R = typeof(op(a[1], b[1]))

    ## this is incorrect because it assumes that `+` calls `promote_type`
    ## but this is not true for some types, such as Bool:
    # R = promote_type(ai, bi)

    # this is wrong, since depending on the return value
    # of type-inference is very brittle (as well as not being optimizable):
    # R = Base.return_types(op, (eltype(a), eltype(b)))

    ## but, finally, this works:
    R = promote_op(op, eltype(a), eltype(b))
    ## although sometimes it may give a larger type than desired
    ## it will always give a correct type

    output = similar(b, R, (size(a, 1), size(b, 2)))
    if size(a, 2) > 0
        for j in 1:size(b, 2)
            for i in 1:size(a, 1)
                ## here we don't use `ab = zero(R)`,
                ## since `R` might be `Any` and `zero(Any)` is not defined
                ## we also must declare `ab::R` to make the type of `ab` constant in the loop,
                ## since it is possible that typeof(a * b) != typeof(a * b + a * b) == R
                ab::R = a[i, 1] * b[1, j]
                for k in 2:size(a, 2)
                    ab += a[i, k] * b[k, j]
                end
                output[i, j] = ab
            end
        end
    end
    return output
end
```

### Separate convert and kernel logic

Una forma de reducir significativamente los tiempos de compilación y la complejidad de las pruebas es aislar la lógica para convertir al tipo deseado y la computación. Esto permite que el compilador especialice e inline la lógica de conversión de manera independiente del resto del cuerpo del kernel más grande.

Este es un patrón común que se observa al convertir de una clase más grande de tipos al tipo de argumento específico que realmente es compatible con el algoritmo:

```julia
complexfunction(arg::Int) = ...
complexfunction(arg::Any) = complexfunction(convert(Int, arg))

matmul(a::T, b::T) = ...
matmul(a, b) = matmul(promote(a, b)...)
```

## Parametrically-constrained Varargs methods

Los parámetros de función también se pueden usar para restringir el número de argumentos que se pueden proporcionar a una función "varargs" ([Varargs Functions](@ref)).  La notación `Vararg{T,N}` se utiliza para indicar tal restricción.  Por ejemplo:

```jldoctest
julia> bar(a,b,x::Vararg{Any,2}) = (a,b,x)
bar (generic function with 1 method)

julia> bar(1,2,3)
ERROR: MethodError: no method matching bar(::Int64, ::Int64, ::Int64)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(::Any, ::Any, ::Any, !Matched::Any)
   @ Main none:1

Stacktrace:
[...]

julia> bar(1,2,3,4)
(1, 2, (3, 4))

julia> bar(1,2,3,4,5)
ERROR: MethodError: no method matching bar(::Int64, ::Int64, ::Int64, ::Int64, ::Int64)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(::Any, ::Any, ::Any, ::Any)
   @ Main none:1

Stacktrace:
[...]
```

Más útilmente, es posible restringir los métodos varargs mediante un parámetro. Por ejemplo:

```julia
function getindex(A::AbstractArray{T,N}, indices::Vararg{Number,N}) where {T,N}
```

se llamaría solo cuando el número de `índices` coincide con la dimensionalidad del arreglo.

Cuando solo se necesita restringir el tipo de los argumentos suministrados, `Vararg{T}` se puede escribir de manera equivalente como `T...`. Por ejemplo, `f(x::Int...) = x` es una forma abreviada de `f(x::Vararg{Int}) = x`.

## Note on Optional and keyword Arguments

Como se mencionó brevemente en [Functions](@ref man-functions), los argumentos opcionales se implementan como una sintaxis para múltiples definiciones de métodos. Por ejemplo, esta definición:

```julia
f(a=1,b=2) = a+2b
```

se traduce a los siguientes tres métodos:

```julia
f(a,b) = a+2b
f(a) = f(a,2)
f() = f(1,2)
```

Esto significa que llamar a `f()` es equivalente a llamar a `f(1,2)`. En este caso, el resultado es `5`, porque `f(1,2)` invoca el primer método de `f` mencionado anteriormente. Sin embargo, esto no siempre tiene que ser así. Si defines un cuarto método que es más especializado para enteros:

```julia
f(a::Int,b::Int) = a-2b
```

entonces el resultado de ambos `f()` y `f(1,2)` es `-3`. En otras palabras, los argumentos opcionales están vinculados a una función, no a ningún método específico de esa función. Depende de los tipos de los argumentos opcionales qué método se invoca. Cuando los argumentos opcionales se definen en términos de una variable global, el tipo del argumento opcional puede incluso cambiar en tiempo de ejecución.

Los argumentos de palabra clave se comportan de manera bastante diferente a los argumentos posicionales ordinarios. En particular, no participan en la selección de métodos. Los métodos se seleccionan únicamente en función de los argumentos posicionales, y los argumentos de palabra clave se procesan después de que se identifica el método coincidente.

## Function-like objects

Los métodos están asociados con tipos, por lo que es posible hacer que cualquier objeto arbitrario de Julia sea "llamable" al agregar métodos a su tipo. (Estos objetos "llamables" a veces se denominan "functores".)

Por ejemplo, puedes definir un tipo que almacene los coeficientes de un polinomio, pero que se comporte como una función que evalúa el polinomio:

```jldoctest polynomial
julia> struct Polynomial{R}
           coeffs::Vector{R}
       end

julia> function (p::Polynomial)(x)
           v = p.coeffs[end]
           for i = (length(p.coeffs)-1):-1:1
               v = v*x + p.coeffs[i]
           end
           return v
       end

julia> (p::Polynomial)() = p(5)
```

Tenga en cuenta que la función se especifica por tipo en lugar de por nombre. Al igual que con las funciones normales, hay una forma de sintaxis concisa. En el cuerpo de la función, `p` se referirá al objeto que fue llamado. Un `Polynomial` se puede usar de la siguiente manera:

```jldoctest polynomial
julia> p = Polynomial([1,10,100])
Polynomial{Int64}([1, 10, 100])

julia> p(3)
931

julia> p()
2551
```

Este mecanismo también es la clave de cómo funcionan los constructores de tipos y los cierres (funciones internas que se refieren a su entorno circundante) en Julia.

## Empty generic functions

Ocasionalmente, es útil introducir una función genérica sin agregar métodos aún. Esto se puede utilizar para separar las definiciones de interfaz de las implementaciones. También se puede hacer con el propósito de documentación o legibilidad del código. La sintaxis para esto es un bloque `function` vacío sin una tupla de argumentos:

```julia
function emptyfunc end
```

## [Method design and the avoidance of ambiguities](@id man-method-design-ambiguities)

El polimorfismo de métodos de Julia es una de sus características más poderosas, sin embargo, aprovechar este poder puede presentar desafíos de diseño. En particular, en jerarquías de métodos más complejas, no es raro que surja [ambiguities](@ref man-ambiguities).

Arriba, se señaló que se pueden resolver ambigüedades como

```julia
f(x, y::Int) = 1
f(x::Int, y) = 2
```

definiendo un método

```julia
f(x::Int, y::Int) = 3
```

Esta suele ser la estrategia correcta; sin embargo, hay circunstancias en las que seguir este consejo sin pensar puede ser contraproducente. En particular, cuantas más métodos tenga una función genérica, más posibilidades hay de ambigüedades. Cuando tus jerarquías de métodos se vuelven más complicadas que este simple ejemplo, puede valer la pena pensar detenidamente en estrategias alternativas.

A continuación, discutimos desafíos particulares y algunas formas alternativas de resolver tales problemas.

### Tuple and NTuple arguments

`Tuple` (y `NTuple`) los argumentos presentan desafíos especiales. Por ejemplo,

```julia
f(x::NTuple{N,Int}) where {N} = 1
f(x::NTuple{N,Float64}) where {N} = 2
```

son ambiguos debido a la posibilidad de que `N == 0`: no hay elementos para determinar si se debe llamar a la variante `Int` o `Float64`. Para resolver la ambigüedad, un enfoque es definir un método para la tupla vacía:

```julia
f(x::Tuple{}) = 3
```

Alternativamente, para todos los métodos excepto uno, puedes insistir en que hay al menos un elemento en la tupla:

```julia
f(x::NTuple{N,Int}) where {N} = 1           # this is the fallback
f(x::Tuple{Float64, Vararg{Float64}}) = 2   # this requires at least one Float64
```

### [Orthogonalize your design](@id man-methods-orthogonalize)

Cuando te sientas tentado a despachar con dos o más argumentos, considera si una función "envoltura" podría hacer que el diseño sea más simple. Por ejemplo, en lugar de escribir múltiples variantes:

```julia
f(x::A, y::A) = ...
f(x::A, y::B) = ...
f(x::B, y::A) = ...
f(x::B, y::B) = ...
```

podrías considerar definir

```julia
f(x::A, y::A) = ...
f(x, y) = f(g(x), g(y))
```

donde `g` convierte el argumento al tipo `A`. Este es un ejemplo muy específico del principio más general de [orthogonal design](https://en.wikipedia.org/wiki/Orthogonality_(programming)), en el que conceptos separados se asignan a métodos separados. Aquí, `g` probablemente necesitará una definición de respaldo.

```julia
g(x::A) = x
```

Una estrategia relacionada explota `promote` para llevar `x` e `y` a un tipo común:

```julia
f(x::T, y::T) where {T} = ...
f(x, y) = f(promote(x, y)...)
```

Un riesgo con este diseño es la posibilidad de que, si no hay un método de promoción adecuado que convierta `x` e `y` al mismo tipo, el segundo método se recursione infinitamente y provoque un desbordamiento de pila.

### Dispatch on one argument at a time

Si necesitas despachar en múltiples argumentos, y hay muchas alternativas con demasiadas combinaciones para hacer práctico definir todas las variantes posibles, entonces considera introducir una "cascada de nombres" donde (por ejemplo) despachas en el primer argumento y luego llamas a un método interno:

```julia
f(x::A, y) = _fA(x, y)
f(x::B, y) = _fB(x, y)
```

Entonces, los métodos internos `_fA` y `_fB` pueden despachar sobre `y` sin preocuparse por ambigüedades entre ellos con respecto a `x`.

Ten en cuenta que esta estrategia tiene al menos una desventaja importante: en muchos casos, no es posible que los usuarios personalicen aún más el comportamiento de `f` definiendo especializaciones adicionales de tu función exportada `f`. En su lugar, tienen que definir especializaciones para tus métodos internos `_fA` y `_fB`, y esto difumina las líneas entre los métodos exportados e internos.

### Abstract containers and element types

Donde sea posible, intenta evitar definir métodos que despachen en tipos de elementos específicos de contenedores abstractos. Por ejemplo,

```julia
-(A::AbstractArray{T}, b::Date) where {T<:Date}
```

genera ambigüedades para cualquiera que defina un método

```julia
-(A::MyArrayType{T}, b::T) where {T}
```

La mejor estrategia es evitar definir *cualquiera* de estos métodos: en su lugar, confíe en un método genérico `-(A::AbstractArray, b)` y asegúrese de que este método esté implementado con llamadas genéricas (como `similar` y `-`) que hagan lo correcto para cada tipo de contenedor y tipo de elemento *por separado*. Esta es solo una variante más compleja del consejo de [orthogonalize](@ref man-methods-orthogonalize) sus métodos.

Cuando este enfoque no es posible, puede valer la pena iniciar una discusión con otros desarrolladores sobre cómo resolver la ambigüedad; solo porque un método se definió primero no significa necesariamente que no se pueda modificar o eliminar. Como último recurso, un desarrollador puede definir el método "curita".

```julia
-(A::MyArrayType{T}, b::Date) where {T<:Date} = ...
```

eso resuelve la ambigüedad por la fuerza bruta.

### Complex method "cascades" with default arguments

Si estás definiendo un método "cascade" que proporciona valores predeterminados, ten cuidado de no omitir ningún argumento que corresponda a posibles valores predeterminados. Por ejemplo, supongamos que estás escribiendo un algoritmo de filtrado digital y tienes un método que maneja los bordes de la señal aplicando relleno:

```julia
function myfilter(A, kernel, ::Replicate)
    Apadded = replicate_edges(A, size(kernel))
    myfilter(Apadded, kernel)  # now perform the "real" computation
end
```

Esto entrará en conflicto con un método que proporciona un relleno predeterminado:

```julia
myfilter(A, kernel) = myfilter(A, kernel, Replicate()) # replicate the edge by default
```

Juntas, estas dos métodos generan una recursión infinita con `A` creciendo constantemente más grande.

El mejor diseño sería definir tu jerarquía de llamadas así:

```julia
struct NoPad end  # indicate that no padding is desired, or that it's already applied

myfilter(A, kernel) = myfilter(A, kernel, Replicate())  # default boundary conditions

function myfilter(A, kernel, ::Replicate)
    Apadded = replicate_edges(A, size(kernel))
    myfilter(Apadded, kernel, NoPad())  # indicate the new boundary conditions
end

# other padding methods go here

function myfilter(A, kernel, ::NoPad)
    # Here's the "real" implementation of the core computation
end
```

`NoPad` se suministra en la misma posición de argumento que cualquier otro tipo de relleno, por lo que mantiene la jerarquía de despacho bien organizada y con una menor probabilidad de ambigüedades. Además, extiende la interfaz "pública" `myfilter`: un usuario que desee controlar el relleno de manera explícita puede llamar a la variante `NoPad` directamente.

## Defining methods in local scope

Puedes definir métodos dentro de un [local scope](@ref scope-of-variables), por ejemplo

```jldoctest
julia> function f(x)
           g(y::Int) = y + x
           g(y) = y - x
           g
       end
f (generic function with 1 method)

julia> h = f(3);

julia> h(4)
7

julia> h(4.0)
1.0
```

Sin embargo, no debes *definir* métodos locales de manera condicional o sujeta al flujo de control, como en

```julia
function f2(inc)
    if inc
        g(x) = x + 1
    else
        g(x) = x - 1
    end
end

function f3()
    function g end
    return g
    g() = 0
end
```

ya que no está claro qué función terminará definiéndose. En el futuro, podría ser un error definir métodos locales de esta manera.

Para casos como este, usa funciones anónimas en su lugar:

```julia
function f2(inc)
    g = if inc
        x -> x + 1
    else
        x -> x - 1
    end
end
```

[^Clarke61]: Arthur C. Clarke, *Profiles of the Future* (1961): Clarke's Third Law.
