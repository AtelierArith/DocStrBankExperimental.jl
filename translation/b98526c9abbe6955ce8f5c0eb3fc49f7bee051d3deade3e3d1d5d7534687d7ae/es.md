# [Constructors](@id man-constructors)

Constructores [^1] son funciones que crean nuevos objetos – específicamente, instancias de [Composite Types](@ref). En Julia, los objetos de tipo también sirven como funciones constructoras: crean nuevas instancias de sí mismos cuando se aplican a una tupla de argumentos como una función. Esto ya se mencionó brevemente cuando se introdujeron los tipos compuestos. Por ejemplo:

```jldoctest footype
julia> struct Foo
           bar
           baz
       end

julia> foo = Foo(1, 2)
Foo(1, 2)

julia> foo.bar
1

julia> foo.baz
2
```

Para muchos tipos, formar nuevos objetos al unir los valores de sus campos es todo lo que se necesita para crear instancias. Sin embargo, en algunos casos se requiere más funcionalidad al crear objetos compuestos. A veces, se deben hacer cumplir invariantes, ya sea verificando argumentos o transformándolos. [Recursive data structures](https://en.wikipedia.org/wiki/Recursion_%28computer_science%29#Recursive_data_structures_.28structural_recursion.29), especialmente aquellos que pueden ser autorreferenciales, a menudo no pueden ser construidos de manera limpia sin ser primero creados en un estado incompleto y luego alterados programáticamente para ser completados, como un paso separado de la creación del objeto. A veces, simplemente es conveniente poder construir objetos con menos o diferentes tipos de parámetros de los que tienen campos. El sistema de Julia para la construcción de objetos aborda todos estos casos y más.

[^1]: Nomenclature: while the term "constructor" generally refers to the entire function which constructs objects of a type, it is common to abuse terminology slightly and refer to specific constructor methods as "constructors". In such situations, it is generally clear from the context that the term is used to mean "constructor method" rather than "constructor function", especially as it is often used in the sense of singling out a particular method of the constructor from all of the others.

## [Outer Constructor Methods](@id man-outer-constructor-methods)

Un constructor es como cualquier otra función en Julia en el sentido de que su comportamiento general está definido por el comportamiento combinado de sus métodos. En consecuencia, puedes agregar funcionalidad a un constructor simplemente definiendo nuevos métodos. Por ejemplo, digamos que quieres agregar un método de constructor para objetos `Foo` que tome solo un argumento y use el valor dado tanto para los campos `bar` como `baz`. Esto es simple:

```jldoctest footype
julia> Foo(x) = Foo(x,x)
Foo

julia> Foo(1)
Foo(1, 1)
```

También podrías agregar un método constructor `Foo` sin argumentos que proporcione valores predeterminados tanto para los campos `bar` como `baz`:

```jldoctest footype
julia> Foo() = Foo(0)
Foo

julia> Foo()
Foo(0, 0)
```

Aquí el método del constructor sin argumentos llama al método del constructor con un solo argumento, que a su vez llama al método del constructor con dos argumentos que se proporciona automáticamente. Por razones que se aclararán muy pronto, los métodos del constructor adicionales declarados como métodos normales como este se llaman *métodos de constructor externos*. Los métodos de constructor externos solo pueden crear una nueva instancia llamando a otro método de constructor, como los que se proporcionan automáticamente por defecto.

## [Inner Constructor Methods](@id man-inner-constructor-methods)

Mientras que los métodos de constructor externos logran abordar el problema de proporcionar métodos de conveniencia adicionales para la construcción de objetos, no logran abordar los otros dos casos de uso mencionados en la introducción de este capítulo: hacer cumplir invariantes y permitir la construcción de objetos autorreferenciales. Para estos problemas, se necesitan *métodos de constructor internos*. Un método de constructor interno es como un método de constructor externo, excepto por dos diferencias:

1. Se declara dentro del bloque de una declaración de tipo, en lugar de fuera de él como los métodos normales.
2. Tiene acceso a una función especial existente localmente llamada [`new`](@ref) que crea objetos del tipo del bloque.

Por ejemplo, supongamos que uno quiere declarar un tipo que contenga un par de números reales, sujeto a la restricción de que el primer número no sea mayor que el segundo. Se podría declarar de esta manera:

```jldoctest pairtype
julia> struct OrderedPair
           x::Real
           y::Real
           OrderedPair(x,y) = x > y ? error("out of order") : new(x,y)
       end
```

Ahora los objetos `OrderedPair` solo se pueden construir de tal manera que `x <= y`:

```jldoctest pairtype; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> OrderedPair(1, 2)
OrderedPair(1, 2)

julia> OrderedPair(2,1)
ERROR: out of order
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] OrderedPair(::Int64, ::Int64) at ./none:4
 [3] top-level scope
```

Si el tipo se declarara como `mutable`, podrías acceder y cambiar directamente los valores de los campos para violar esta invariante. Por supuesto, jugar con los internos de un objeto sin invitación es una mala práctica. Tú (o alguien más) también pueden proporcionar métodos de constructor externos adicionales en cualquier momento posterior, pero una vez que un tipo es declarado, no hay forma de agregar más métodos de constructor internos. Dado que los métodos de constructor externos solo pueden crear objetos llamando a otros métodos de constructor, en última instancia, debe llamarse algún constructor interno para crear un objeto. Esto garantiza que todos los objetos del tipo declarado deben existir a través de una llamada a uno de los métodos de constructor internos proporcionados con el tipo, lo que otorga un cierto grado de cumplimiento de las invariantes de un tipo.

Si se define algún método de constructor interno, no se proporciona un método de constructor por defecto: se presume que te has provisto de todos los constructores internos que necesitas. El constructor por defecto es equivalente a escribir tu propio método de constructor interno que toma todos los campos del objeto como parámetros (constriñéndose a ser del tipo correcto, si el campo correspondiente tiene un tipo) y los pasa a `new`, devolviendo el objeto resultante:

```jldoctest
julia> struct Foo
           bar
           baz
           Foo(bar,baz) = new(bar,baz)
       end

```

Esta declaración tiene el mismo efecto que la definición anterior del tipo `Foo` sin un método de constructor interno explícito. Los siguientes dos tipos son equivalentes: uno con un constructor predeterminado, el otro con un constructor explícito:

```jldoctest
julia> struct T1
           x::Int64
       end

julia> struct T2
           x::Int64
           T2(x) = new(x)
       end

julia> T1(1)
T1(1)

julia> T2(1)
T2(1)

julia> T1(1.0)
T1(1)

julia> T2(1.0)
T2(1)
```

Es una buena práctica proporcionar la menor cantidad posible de métodos de constructor internos: solo aquellos que toman todos los argumentos de manera explícita y que imponen una verificación de errores y transformación esenciales. Los métodos de constructor de conveniencia adicionales, que suministran valores predeterminados o transformaciones auxiliares, deben proporcionarse como constructores externos que llaman a los constructores internos para realizar el trabajo pesado. Esta separación es típicamente bastante natural.

## Incomplete Initialization

El problema final que aún no se ha abordado es la construcción de objetos autorreferenciales, o más generalmente, estructuras de datos recursivas. Dado que la dificultad fundamental puede no ser inmediatamente obvia, permítanos explicarlo brevemente. Considere la siguiente declaración de tipo recursivo:

```jldoctest selfrefer
julia> mutable struct SelfReferential
           obj::SelfReferential
       end

```

Este tipo puede parecer lo suficientemente inocuo, hasta que uno considera cómo construir una instancia de él. Si `a` es una instancia de `SelfReferential`, entonces se puede crear una segunda instancia con la llamada:

```julia-repl
julia> b = SelfReferential(a)
```

Pero, ¿cómo se construye la primera instancia cuando no existe ninguna instancia que proporcione un valor válido para su campo `obj`? La única solución es permitir la creación de una instancia incompletamente inicializada de `SelfReferential` con un campo `obj` no asignado, y usar esa instancia incompleta como un valor válido para el campo `obj` de otra instancia, como, por ejemplo, la misma.

Para permitir la creación de objetos incompletamente inicializados, Julia permite que se llame a la función [`new`](@ref) con menos campos de los que tiene el tipo, devolviendo un objeto con los campos no especificados no inicializados. El método del constructor interno puede entonces usar el objeto incompleto, completando su inicialización antes de devolverlo. Aquí, por ejemplo, hay otro intento de definir el tipo `SelfReferential`, esta vez utilizando un constructor interno sin argumentos que devuelve instancias con campos `obj` que apuntan a sí mismos:

```jldoctest selfrefer2
julia> mutable struct SelfReferential
           obj::SelfReferential
           SelfReferential() = (x = new(); x.obj = x)
       end

```

Podemos verificar que este constructor funciona y construye objetos que son, de hecho, autorreferenciales:

```jldoctest selfrefer2
julia> x = SelfReferential();

julia> x === x
true

julia> x === x.obj
true

julia> x === x.obj.obj
true
```

Aunque generalmente es una buena idea devolver un objeto completamente inicializado desde un constructor interno, es posible devolver objetos incompletamente inicializados:

```jldoctest incomplete
julia> mutable struct Incomplete
           data
           Incomplete() = new()
       end

julia> z = Incomplete();
```

Mientras se te permite crear objetos con campos no inicializados, cualquier acceso a una referencia no inicializada es un error inmediato:

```jldoctest incomplete
julia> z.data
ERROR: UndefRefError: access to undefined reference
```

Esto evita la necesidad de comprobar continuamente si hay valores `null`. Sin embargo, no todos los campos de objeto son referencias. Julia considera que algunos tipos son "datos simples", lo que significa que todos sus datos son autónomos y no hacen referencia a otros objetos. Los tipos de datos simples consisten en tipos primitivos (por ejemplo, `Int`) y estructuras inmutables de otros tipos de datos simples (ver también: [`isbits`](@ref), [`isbitstype`](@ref)). El contenido inicial de un tipo de datos simple es indefinido:

```julia-repl
julia> struct HasPlain
           n::Int
           HasPlain() = new()
       end

julia> HasPlain()
HasPlain(438103441441)
```

Los arreglos de tipos de datos simples exhiben el mismo comportamiento.

Puedes pasar objetos incompletos a otras funciones desde constructores internos para delegar su finalización:

```jldoctest
julia> mutable struct Lazy
           data
           Lazy(v) = complete_me(new(), v)
       end
```

Al igual que con los objetos incompletos devueltos de los constructores, si `complete_me` o cualquiera de sus llamadas intenta acceder al campo `data` del objeto `Lazy` antes de que haya sido inicializado, se lanzará un error de inmediato.

## Parametric Constructors

Los tipos paramétricos añaden algunas complicaciones a la historia del constructor. Recuerda de [Parametric Types](@ref) que, por defecto, las instancias de tipos compuestos paramétricos pueden ser construidas ya sea con parámetros de tipo dados explícitamente o con parámetros de tipo implícitos por los tipos de los argumentos dados al constructor. Aquí hay algunos ejemplos:

```jldoctest parametric; filter = r"Closest candidates.*\n  .*"
julia> struct Point{T<:Real}
           x::T
           y::T
       end

julia> Point(1,2) ## implicit T ##
Point{Int64}(1, 2)

julia> Point(1.0,2.5) ## implicit T ##
Point{Float64}(1.0, 2.5)

julia> Point(1,2.5) ## implicit T ##
ERROR: MethodError: no method matching Point(::Int64, ::Float64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, ::T) where T<:Real at none:2

julia> Point{Int64}(1, 2) ## explicit T ##
Point{Int64}(1, 2)

julia> Point{Int64}(1.0,2.5) ## explicit T ##
ERROR: InexactError: Int64(2.5)
Stacktrace:
[...]

julia> Point{Float64}(1.0, 2.5) ## explicit T ##
Point{Float64}(1.0, 2.5)

julia> Point{Float64}(1,2) ## explicit T ##
Point{Float64}(1.0, 2.0)
```

Como puedes ver, para las llamadas al constructor con parámetros de tipo explícitos, los argumentos se convierten a los tipos de campo implícitos: `Point{Int64}(1,2)` funciona, pero `Point{Int64}(1.0,2.5)` genera un [`InexactError`](@ref) al convertir `2.5` a [`Int64`](@ref). Cuando el tipo es implícito por los argumentos de la llamada al constructor, como en `Point(1,2)`, entonces los tipos de los argumentos deben coincidir; de lo contrario, no se puede determinar el `T` – pero cualquier par de argumentos reales con tipo coincidente puede ser dado al constructor genérico `Point`.

Lo que realmente está sucediendo aquí es que `Point`, `Point{Float64}` y `Point{Int64}` son todas diferentes funciones constructoras. De hecho, `Point{T}` es una función constructora distinta para cada tipo `T`. Sin ningún constructor interno proporcionado explícitamente, la declaración del tipo compuesto `Point{T<:Real}` proporciona automáticamente un constructor interno, `Point{T}`, para cada tipo posible `T<:Real`, que se comporta de la misma manera que lo hacen los constructores internos predeterminados no paramétricos. También proporciona un único constructor externo general `Point` que toma pares de argumentos reales, que deben ser del mismo tipo. Esta provisión automática de constructores es equivalente a la siguiente declaración explícita:

```jldoctest parametric2
julia> struct Point{T<:Real}
           x::T
           y::T
           Point{T}(x,y) where {T<:Real} = new(x,y)
       end

julia> Point(x::T, y::T) where {T<:Real} = Point{T}(x,y);
```

Nota que cada definición tiene la forma de la llamada al constructor que maneja. La llamada `Point{Int64}(1,2)` invocará la definición `Point{T}(x,y)` dentro del bloque `struct`. La declaración del constructor externo, por otro lado, define un método para el constructor general `Point` que solo se aplica a pares de valores del mismo tipo real. Esta declaración permite que las llamadas al constructor sin parámetros de tipo explícitos, como `Point(1,2)` y `Point(1.0,2.5)`, funcionen. Dado que la declaración del método restringe los argumentos a ser del mismo tipo, llamadas como `Point(1,2.5)`, con argumentos de diferentes tipos, resultan en errores de "sin método".

Supongamos que queremos hacer que la llamada al constructor `Point(1,2.5)` funcione "promoviendo" el valor entero `1` al valor de punto flotante `1.0`. La forma más sencilla de lograr esto es definir el siguiente método de constructor externo adicional:

```jldoctest parametric2
julia> Point(x::Int64, y::Float64) = Point(convert(Float64,x),y);
```

Este método utiliza la función [`convert`](@ref) para convertir explícitamente `x` a [`Float64`](@ref) y luego delega la construcción al constructor general para el caso en que ambos argumentos son `4d61726b646f776e2e436f64652822222c2022466c6f617436342229_40726566`. Con esta definición de método, lo que anteriormente era un [`MethodError`](@ref) ahora crea exitosamente un punto de tipo `Point{Float64}`:

```jldoctest parametric2
julia> p = Point(1,2.5)
Point{Float64}(1.0, 2.5)

julia> typeof(p)
Point{Float64}
```

Sin embargo, otras llamadas similares aún no funcionan:

```jldoctest parametric2
julia> Point(1.5,2)
ERROR: MethodError: no method matching Point(::Float64, ::Int64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, !Matched::T) where T<:Real
   @ Main none:1
  Point(!Matched::Int64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]
```

For a more general way to make all such calls work sensibly, see [Conversion and Promotion](@ref conversion-and-promotion). At the risk of spoiling the suspense, we can reveal here that all it takes is the following outer method definition to make all calls to the general `Point` constructor work as one would expect:

```jldoctest parametric2
julia> Point(x::Real, y::Real) = Point(promote(x,y)...);
```

La función `promote` convierte todos sus argumentos a un tipo común; en este caso [`Float64`](@ref). Con esta definición de método, el constructor `Point` promueve sus argumentos de la misma manera que lo hacen los operadores numéricos como [`+`](@ref), y funciona para todo tipo de números reales:

```jldoctest parametric2
julia> Point(1.5,2)
Point{Float64}(1.5, 2.0)

julia> Point(1,1//2)
Point{Rational{Int64}}(1//1, 1//2)

julia> Point(1.0,1//2)
Point{Float64}(1.0, 0.5)
```

Así, aunque los constructores de parámetros de tipo implícitos proporcionados por defecto en Julia son bastante estrictos, es posible hacer que se comporten de una manera más relajada pero sensata con bastante facilidad. Además, dado que los constructores pueden aprovechar todo el poder del sistema de tipos, los métodos y el despacho múltiple, definir un comportamiento sofisticado suele ser bastante simple.

## Case Study: Rational

Quizás la mejor manera de unir todas estas piezas es presentar un ejemplo del mundo real de un tipo compuesto paramétrico y sus métodos de constructor. Con ese fin, implementamos nuestro propio tipo de número racional `OurRational`, similar al tipo [`Rational`](@ref) incorporado en Julia, definido en [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl):

```jldoctest rational
julia> struct OurRational{T<:Integer} <: Real
           num::T
           den::T
           function OurRational{T}(num::T, den::T) where T<:Integer
               if num == 0 && den == 0
                    error("invalid rational: 0//0")
               end
               num = flipsign(num, den)
               den = flipsign(den, den)
               g = gcd(num, den)
               num = div(num, g)
               den = div(den, g)
               new(num, den)
           end
       end

julia> OurRational(n::T, d::T) where {T<:Integer} = OurRational{T}(n,d)
OurRational

julia> OurRational(n::Integer, d::Integer) = OurRational(promote(n,d)...)
OurRational

julia> OurRational(n::Integer) = OurRational(n,one(n))
OurRational

julia> ⊘(n::Integer, d::Integer) = OurRational(n,d)
⊘ (generic function with 1 method)

julia> ⊘(x::OurRational, y::Integer) = x.num ⊘ (x.den*y)
⊘ (generic function with 2 methods)

julia> ⊘(x::Integer, y::OurRational) = (x*y.den) ⊘ y.num
⊘ (generic function with 3 methods)

julia> ⊘(x::Complex, y::Real) = complex(real(x) ⊘ y, imag(x) ⊘ y)
⊘ (generic function with 4 methods)

julia> ⊘(x::Real, y::Complex) = (x*y') ⊘ real(y*y')
⊘ (generic function with 5 methods)

julia> function ⊘(x::Complex, y::Complex)
           xy = x*y'
           yy = real(y*y')
           complex(real(xy) ⊘ yy, imag(xy) ⊘ yy)
       end
⊘ (generic function with 6 methods)
```

La primera línea – `struct OurRational{T<:Integer} <: Real` – declara que `OurRational` toma un parámetro de tipo de un tipo entero, y es en sí mismo un tipo real. Las declaraciones de campo `num::T` y `den::T` indican que los datos contenidos en un objeto `OurRational{T}` son un par de enteros del tipo `T`, uno representando el numerador del valor racional y el otro representando su denominador.

Ahora las cosas se ponen interesantes. `OurRational` tiene un único método de constructor interno que verifica que `num` y `den` no sean ambos cero y asegura que cada racional se construya en "términos más bajos" con un denominador no negativo. Esto se logra primero invirtiendo los signos del numerador y del denominador si el denominador es negativo. Luego, ambos se dividen por su máximo común divisor (`gcd` siempre devuelve un número no negativo, independientemente del signo de sus argumentos). Dado que este es el único constructor interno para `OurRational`, podemos estar seguros de que los objetos `OurRational` siempre se construyen en esta forma normalizada.

`OurRational` también proporciona varios métodos de constructor externo para mayor comodidad. El primero es el constructor general "estándar" que infiere el parámetro de tipo `T` del tipo del numerador y el denominador cuando tienen el mismo tipo. El segundo se aplica cuando los valores de numerador y denominador dados tienen tipos diferentes: los promueve a un tipo común y luego delega la construcción al constructor externo para argumentos de tipo coincidente. El tercer constructor externo convierte valores enteros en racionales al suministrar un valor de `1` como denominador.

Siguiendo las definiciones del constructor externo, definimos una serie de métodos para el operador `⊘`, que proporciona una sintaxis para escribir racionales (por ejemplo, `1 ⊘ 2`). El tipo `Rational` de Julia utiliza el operador [`//`](@ref) para este propósito. Antes de estas definiciones, `⊘` es un operador completamente indefinido con solo sintaxis y sin significado. Después, se comporta tal como se describe en [Rational Numbers](@ref) – su comportamiento completo está definido en estas pocas líneas. Tenga en cuenta que el uso infijo de `⊘` funciona porque Julia tiene un conjunto de símbolos que se reconocen como operadores infijos. La primera y más básica definición simplemente hace que `a ⊘ b` construya un `OurRational` aplicando el constructor `OurRational` a `a` y `b` cuando son enteros. Cuando uno de los operandos de `⊘` ya es un número racional, construimos un nuevo racional para la relación resultante de manera ligeramente diferente; este comportamiento es en realidad idéntico a la división de un racional con un entero. Finalmente, aplicar `⊘` a valores enteros complejos crea una instancia de `Complex{<:OurRational}` – un número complejo cuyas partes real e imaginaria son racionales:

```jldoctest rational
julia> z = (1 + 2im) ⊘ (1 - 2im);

julia> typeof(z)
Complex{OurRational{Int64}}

julia> typeof(z) <: Complex{<:OurRational}
true
```

Así, aunque el operador `⊘` generalmente devuelve una instancia de `OurRational`, si alguno de sus argumentos son enteros complejos, devolverá una instancia de `Complex{<:OurRational}` en su lugar. El lector interesado debería considerar revisar el resto de [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl): es corto, autónomo e implementa un tipo básico completo de Julia.

## Outer-only constructors

Como hemos visto, un tipo paramétrico típico tiene constructores internos que se llaman cuando se conocen los parámetros de tipo; por ejemplo, se aplican a `Point{Int}` pero no a `Point`. Opcionalmente, se pueden agregar constructores externos que determinan automáticamente los parámetros de tipo, por ejemplo, construyendo un `Point{Int}` a partir de la llamada `Point(1,2)`. Los constructores externos llaman a los constructores internos para crear instancias. Sin embargo, en algunos casos, uno preferiría no proporcionar constructores internos, de modo que no se puedan solicitar manualmente parámetros de tipo específicos.

Por ejemplo, digamos que definimos un tipo que almacena un vector junto con una representación precisa de su suma:

```jldoctest
julia> struct SummedArray{T<:Number,S<:Number}
           data::Vector{T}
           sum::S
       end

julia> SummedArray(Int32[1; 2; 3], Int32(6))
SummedArray{Int32, Int32}(Int32[1, 2, 3], 6)
```

El problema es que queremos que `S` sea un tipo más grande que `T`, para que podamos sumar muchos elementos con menos pérdida de información. Por ejemplo, cuando `T` es [`Int32`](@ref), nos gustaría que `S` fuera [`Int64`](@ref). Por lo tanto, queremos evitar una interfaz que permita al usuario construir instancias del tipo `SummedArray{Int32,Int32}`. Una forma de hacer esto es proporcionar un constructor solo para `SummedArray`, pero dentro del bloque de definición de `struct` suprimir la generación de constructores predeterminados:

```jldoctest
julia> struct SummedArray{T<:Number,S<:Number}
           data::Vector{T}
           sum::S
           function SummedArray(a::Vector{T}) where T
               S = widen(T)
               new{T,S}(a, sum(S, a))
           end
       end

julia> SummedArray(Int32[1; 2; 3], Int32(6))
ERROR: MethodError: no method matching SummedArray(::Vector{Int32}, ::Int32)
The type `SummedArray` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  SummedArray(::Vector{T}) where T
   @ Main none:4

Stacktrace:
[...]
```

Este constructor será invocado por la sintaxis `SummedArray(a)`. La sintaxis `new{T,S}` permite especificar parámetros para el tipo que se va a construir, es decir, esta llamada devolverá un `SummedArray{T,S}`. `new{T,S}` se puede utilizar en cualquier definición de constructor, pero por conveniencia, los parámetros de `new{}` se derivan automáticamente del tipo que se está construyendo cuando es posible.

## Constructors are just callable objects

Un objeto de cualquier tipo puede ser [made callable](@ref "Function-like objects") al definir un método. Esto incluye tipos, es decir, objetos del tipo [`Type`](@ref); y los constructores pueden, de hecho, ser vistos simplemente como objetos de tipo llamables. Por ejemplo, hay muchos métodos definidos en `Bool` y varios supertipos de este:

```julia-repl
julia> methods(Bool)
# 10 methods for type constructor:
  [1] Bool(x::BigFloat)
     @ Base.MPFR mpfr.jl:393
  [2] Bool(x::Float16)
     @ Base float.jl:338
  [3] Bool(x::Rational)
     @ Base rational.jl:138
  [4] Bool(x::Real)
     @ Base float.jl:233
  [5] (dt::Type{<:Integer})(ip::Sockets.IPAddr)
     @ Sockets ~/tmp/jl/jl/julia-nightly-assert/share/julia/stdlib/v1.11/Sockets/src/IPAddr.jl:11
  [6] (::Type{T})(x::Enum{T2}) where {T<:Integer, T2<:Integer}
     @ Base.Enums Enums.jl:19
  [7] (::Type{T})(z::Complex) where T<:Real
     @ Base complex.jl:44
  [8] (::Type{T})(x::Base.TwicePrecision) where T<:Number
     @ Base twiceprecision.jl:265
  [9] (::Type{T})(x::T) where T<:Number
     @ boot.jl:894
 [10] (::Type{T})(x::AbstractChar) where T<:Union{AbstractChar, Number}
     @ char.jl:50
```

La sintaxis habitual del constructor es exactamente equivalente a la sintaxis de objeto tipo función, por lo que intentar definir un método con cada sintaxis hará que el primer método sea sobrescrito por el siguiente:

```jldoctest
julia> struct S
           f::Int
       end

julia> S() = S(7)
S

julia> (::Type{S})() = S(8)  # overwrites the previous constructor method

julia> S()
S(8)
```
