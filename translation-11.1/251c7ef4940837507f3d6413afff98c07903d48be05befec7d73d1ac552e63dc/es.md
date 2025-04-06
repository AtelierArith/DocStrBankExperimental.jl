# [Conversion and Promotion](@id conversion-and-promotion)

Julia tiene un sistema para promover argumentos de operadores matemáticos a un tipo común, que se ha mencionado en varias otras secciones, incluyendo [Integers and Floating-Point Numbers](@ref), [Mathematical Operations and Elementary Functions](@ref), [Types](@ref man-types), y [Methods](@ref). En esta sección, explicamos cómo funciona este sistema de promoción, así como cómo extenderlo a nuevos tipos y aplicarlo a funciones además de los operadores matemáticos incorporados. Tradicionalmente, los lenguajes de programación se dividen en dos grupos con respecto a la promoción de argumentos aritméticos:

  * **Promoción automática para tipos aritméticos integrados y operadores.** En la mayoría de los lenguajes, los tipos numéricos integrados, cuando se utilizan como operandos de operadores aritméticos con sintaxis infija, como `+`, `-`, `*` y `/`, se promueven automáticamente a un tipo común para producir los resultados esperados. C, Java, Perl y Python, por nombrar algunos, calculan correctamente la suma `1 + 1.5` como el valor de punto flotante `2.5`, a pesar de que uno de los operandos de `+` es un entero. Estos sistemas son convenientes y están diseñados con suficiente cuidado para que generalmente sean casi invisibles para el programador: casi nadie piensa conscientemente en esta promoción que ocurre al escribir tal expresión, pero los compiladores e intérpretes deben realizar la conversión antes de la adición, ya que los enteros y los valores de punto flotante no se pueden sumar tal como están. Por lo tanto, las reglas complejas para tales conversiones automáticas son inevitablemente parte de las especificaciones e implementaciones de tales lenguajes.
  * **No promoción automática.** Este campamento incluye Ada y ML, lenguajes de programación de tipos estáticos muy "estrictos". En estos lenguajes, cada conversión debe ser especificada explícitamente por el programador. Así, la expresión de ejemplo `1 + 1.5` generaría un error de compilación tanto en Ada como en ML. En su lugar, uno debe escribir `real(1) + 1.5`, convirtiendo explícitamente el entero `1` a un valor de punto flotante antes de realizar la suma. Sin embargo, la conversión explícita en todas partes es tan inconveniente que incluso Ada tiene cierto grado de conversión automática: los literales enteros se promueven al tipo entero esperado automáticamente, y los literales de punto flotante se promueven de manera similar a los tipos de punto flotante apropiados.

En cierto sentido, Julia cae en la categoría de "sin promoción automática": los operadores matemáticos son solo funciones con una sintaxis especial, y los argumentos de las funciones nunca se convierten automáticamente. Sin embargo, se puede observar que aplicar operaciones matemáticas a una amplia variedad de tipos de argumentos mixtos es solo un caso extremo de despacho múltiple polimórfico, algo para lo cual los sistemas de despacho y tipos de Julia están particularmente bien equipados. La promoción "automática" de los operandos matemáticos simplemente surge como una aplicación especial: Julia viene con reglas de despacho predefinidas que abarcan todos los casos para los operadores matemáticos, invocadas cuando no existe una implementación específica para alguna combinación de tipos de operandos. Estas reglas de captura primero promueven todos los operandos a un tipo común utilizando reglas de promoción definidas por el usuario, y luego invocan una implementación especializada del operador en cuestión para los valores resultantes, ahora del mismo tipo. Los tipos definidos por el usuario pueden participar fácilmente en este sistema de promoción definiendo métodos para la conversión hacia y desde otros tipos, y proporcionando un puñado de reglas de promoción que definen a qué tipos deben promoverse cuando se mezclan con otros tipos.

## Conversion

La forma estándar de obtener un valor de un tipo determinado `T` es llamar al constructor del tipo, `T(x)`. Sin embargo, hay casos en los que es conveniente convertir un valor de un tipo a otro sin que el programador lo pida explícitamente. Un ejemplo es asignar un valor a un arreglo: si `A` es un `Vector{Float64}`, la expresión `A[1] = 2` debería funcionar convirtiendo automáticamente el `2` de `Int` a `Float64`, y almacenando el resultado en el arreglo. Esto se hace a través de la función [`convert`](@ref).

La función `convert` generalmente toma dos argumentos: el primero es un objeto de tipo y el segundo es un valor para convertir a ese tipo. El valor devuelto es el valor convertido a una instancia del tipo dado. La forma más sencilla de entender esta función es verla en acción:

```jldoctest
julia> x = 12
12

julia> typeof(x)
Int64

julia> xu = convert(UInt8, x)
0x0c

julia> typeof(xu)
UInt8

julia> xf = convert(AbstractFloat, x)
12.0

julia> typeof(xf)
Float64

julia> a = Any[1 2 3; 4 5 6]
2×3 Matrix{Any}:
 1  2  3
 4  5  6

julia> convert(Array{Float64}, a)
2×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
```

La conversión no siempre es posible, en cuyo caso se lanza un [`MethodError`](@ref) que indica que `convert` no sabe cómo realizar la conversión solicitada:

```jldoctest
julia> convert(AbstractFloat, "foo")
ERROR: MethodError: Cannot `convert` an object of type String to an object of type AbstractFloat
[...]
```

Algunos lenguajes consideran que analizar cadenas como números o formatear números como cadenas son conversiones (muchos lenguajes dinámicos incluso realizarán la conversión automáticamente por ti). Este no es el caso en Julia. Aunque algunas cadenas pueden ser analizadas como números, la mayoría de las cadenas no son representaciones válidas de números, y solo un subconjunto muy limitado de ellas lo es. Por lo tanto, en Julia se debe utilizar la función dedicada [`parse`](@ref) para realizar esta operación, haciéndola más explícita.

### When is `convert` called?

Las siguientes construcciones de lenguaje llaman a `convert`:

  * Asignar a un arreglo convierte al tipo de elemento del arreglo.
  * Asignar a un campo de un objeto se convierte en el tipo declarado del campo.
  * Construyendo un objeto con [`new`](@ref) se convierte en los tipos de campo declarados del objeto.
  * Asignar a una variable con un tipo declarado (por ejemplo, `local x::T`) se convierte en ese tipo.
  * Una función con un tipo de retorno declarado convierte su valor de retorno a ese tipo.
  * Pasar un valor a [`ccall`](@ref) lo convierte en el tipo de argumento correspondiente.

### Conversion vs. Construction

Tenga en cuenta que el comportamiento de `convert(T, x)` parece ser casi idéntico a `T(x)`. De hecho, generalmente lo es. Sin embargo, hay una diferencia semántica clave: dado que `convert` se puede llamar implícitamente, sus métodos están restringidos a casos que se consideran "seguros" o "no sorprendentes". `convert` solo convertirá entre tipos que representen el mismo tipo básico de cosa (por ejemplo, diferentes representaciones de números o diferentes codificaciones de cadenas). También suele ser sin pérdida; convertir un valor a un tipo diferente y volver a convertirlo debería resultar en el mismo valor exacto.

Hay cuatro tipos generales de casos en los que los constructores difieren de `convert`:

#### Constructors for types unrelated to their arguments

Algunos constructores no implementan el concepto de "conversión". Por ejemplo, `Timer(2)` crea un temporizador de 2 segundos, que no es realmente una "conversión" de un entero a un temporizador.

#### Mutable collections

`convert(T, x)` se espera que devuelva el original `x` si `x` ya es del tipo `T`. En contraste, si `T` es un tipo de colección mutable, entonces `T(x)` siempre debería crear una nueva colección (copiando elementos de `x`).

#### Wrapper types

Para algunos tipos que "envuelven" otros valores, el constructor puede envolver su argumento dentro de un nuevo objeto incluso si ya es del tipo solicitado. Por ejemplo, `Some(x)` envuelve `x` para indicar que un valor está presente (en un contexto donde el resultado podría ser un `Some` o `nothing`). Sin embargo, `x` en sí mismo podría ser el objeto `Some(y)`, en cuyo caso el resultado es `Some(Some(y))`, con dos niveles de envoltura. `convert(Some, x)`, por otro lado, simplemente devolvería `x` ya que ya es un `Some`.

#### Constructors that don't return instances of their own type

En *casos muy raros* puede tener sentido que el constructor `T(x)` devuelva un objeto que no sea del tipo `T`. Esto podría suceder si un tipo envoltorio es su propio inverso (por ejemplo, `Flip(Flip(x)) === x`), o para soportar una sintaxis de llamada antigua por compatibilidad hacia atrás cuando se reestructura una biblioteca. Pero `convert(T, x)` siempre debería devolver un valor del tipo `T`.

### Defining New Conversions

Al definir un nuevo tipo, inicialmente todas las formas de crearlo deben definirse como constructores. Si se hace evidente que la conversión implícita sería útil, y que algunos constructores cumplen con los criterios de "seguridad" mencionados anteriormente, entonces se pueden agregar métodos `convert`. Estos métodos son típicamente bastante simples, ya que solo necesitan llamar al constructor apropiado. Tal definición podría verse así:

```julia
import Base: convert
convert(::Type{MyType}, x) = MyType(x)
```

El tipo del primer argumento de este método es [`Type{MyType}`](@ref man-typet-type), la única instancia de la cual es `MyType`. Por lo tanto, este método solo se invoca cuando el primer argumento es el valor de tipo `MyType`. Nota la sintaxis utilizada para el primer argumento: el nombre del argumento se omite antes del símbolo `::`, y solo se da el tipo. Esta es la sintaxis en Julia para un argumento de función cuyo tipo está especificado pero cuyo valor no necesita ser referenciado por nombre.

Todas las instancias de algunos tipos abstractos se consideran por defecto "suficientemente similares" de modo que se proporciona una definición universal de `convert` en Julia Base. Por ejemplo, esta definición establece que es válido `convert` cualquier tipo `Number` a cualquier otro llamando a un constructor de 1 argumento:

```julia
convert(::Type{T}, x::Number) where {T<:Number} = T(x)::T
```

Esto significa que los nuevos tipos `Number` solo necesitan definir constructores, ya que esta definición manejará `convert` por ellos. También se proporciona una conversión de identidad para manejar el caso en el que el argumento ya es del tipo solicitado:

```julia
convert(::Type{T}, x::T) where {T<:Number} = x
```

Existen definiciones similares para `AbstractString`, [`AbstractArray`](@ref), y [`AbstractDict`](@ref).

## Promotion

La promoción se refiere a convertir valores de tipos mixtos a un único tipo común. Aunque no es estrictamente necesario, generalmente se implica que el tipo común al que se convierten los valores puede representar fielmente todos los valores originales. En este sentido, el término "promoción" es apropiado ya que los valores se convierten a un tipo "mayor", es decir, uno que puede representar todos los valores de entrada en un único tipo común. Sin embargo, es importante no confundir esto con la supertipificación orientada a objetos (estructural), o la noción de supertipos abstractos de Julia: la promoción no tiene nada que ver con la jerarquía de tipos, y todo que ver con la conversión entre representaciones alternativas. Por ejemplo, aunque cada valor [`Int32`](@ref) también puede ser representado como un valor [`Float64`](@ref), `Int32` no es un subtipo de `Float64`.

La promoción a un tipo "mayor" común se realiza en Julia mediante la función [`promote`](@ref), que toma cualquier número de argumentos y devuelve una tupla con la misma cantidad de valores, convertidos a un tipo común, o lanza una excepción si la promoción no es posible. El caso de uso más común para la promoción es convertir argumentos numéricos a un tipo común:

```jldoctest
julia> promote(1, 2.5)
(1.0, 2.5)

julia> promote(1, 2.5, 3)
(1.0, 2.5, 3.0)

julia> promote(2, 3//4)
(2//1, 3//4)

julia> promote(1, 2.5, 3, 3//4)
(1.0, 2.5, 3.0, 0.75)

julia> promote(1.5, im)
(1.5 + 0.0im, 0.0 + 1.0im)

julia> promote(1 + 2im, 3//4)
(1//1 + 2//1*im, 3//4 + 0//1*im)
```

Los valores de punto flotante se promueven al más grande de los tipos de argumento de punto flotante. Los valores enteros se promueven al más grande de los tipos de argumento entero. Si los tipos son del mismo tamaño pero difieren en signo, se elige el tipo sin signo. Las mezclas de enteros y valores de punto flotante se promueven a un tipo de punto flotante lo suficientemente grande como para contener todos los valores. Los enteros mezclados con racionales se promueven a racionales. Los racionales mezclados con flotantes se promueven a flotantes. Los valores complejos mezclados con valores reales se promueven al tipo apropiado de valor complejo.

Eso es realmente todo lo que hay que saber sobre el uso de promociones. El resto es solo una cuestión de aplicación ingeniosa, siendo la aplicación "ingeniosa" más típica la definición de métodos generales para operaciones numéricas como los operadores aritméticos `+`, `-`, `*` y `/`. Aquí están algunas de las definiciones de métodos generales dadas en [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl):

```julia
+(x::Number, y::Number) = +(promote(x,y)...)
-(x::Number, y::Number) = -(promote(x,y)...)
*(x::Number, y::Number) = *(promote(x,y)...)
/(x::Number, y::Number) = /(promote(x,y)...)
```

Estas definiciones de métodos dicen que, en ausencia de reglas más específicas para sumar, restar, multiplicar y dividir pares de valores numéricos, se promueven los valores a un tipo común y luego se intenta de nuevo. Eso es todo: en ningún otro lugar uno necesita preocuparse por la promoción a un tipo numérico común para las operaciones aritméticas; simplemente sucede automáticamente. Hay definiciones de métodos de promoción que abarcan una serie de otras funciones aritméticas y matemáticas en [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl), pero más allá de eso, rara vez se requieren llamadas a `promote` en Julia Base. Los usos más comunes de `promote` ocurren en métodos de constructores externos, proporcionados por conveniencia, para permitir que las llamadas a constructores con tipos mixtos deleguen a un tipo interno con campos promovidos a un tipo común apropiado. Por ejemplo, recuerda que [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl) proporciona el siguiente método de constructor externo:

```julia
Rational(n::Integer, d::Integer) = Rational(promote(n,d)...)
```

Esto permite que llamadas como las siguientes funcionen:

```jldoctest
julia> x = Rational(Int8(15),Int32(-5))
-3//1

julia> typeof(x)
Rational{Int32}
```

Para la mayoría de los tipos definidos por el usuario, es una mejor práctica requerir que los programadores suministren los tipos esperados a las funciones constructoras de manera explícita, pero a veces, especialmente para problemas numéricos, puede ser conveniente hacer la promoción automáticamente.

### Defining Promotion Rules

Aunque, en principio, se podrían definir métodos para la función `promote` directamente, esto requeriría muchas definiciones redundantes para todas las posibles permutaciones de tipos de argumentos. En cambio, el comportamiento de `promote` se define en términos de una función auxiliar llamada [`promote_rule`](@ref), para la cual se pueden proporcionar métodos. La función `promote_rule` toma un par de objetos de tipo y devuelve otro objeto de tipo, de modo que las instancias de los tipos de argumento se promoverán al tipo devuelto. Así, al definir la regla:

```julia
import Base: promote_rule
promote_rule(::Type{Float64}, ::Type{Float32}) = Float64
```

uno declara que cuando los valores de punto flotante de 64 bits y 32 bits se promocionan juntos, deben ser promovidos a punto flotante de 64 bits. El tipo de promoción no necesita ser uno de los tipos de argumento. Por ejemplo, las siguientes reglas de promoción ocurren en Julia Base:

```julia
promote_rule(::Type{BigInt}, ::Type{Float64}) = BigFloat
promote_rule(::Type{BigInt}, ::Type{Int8}) = BigInt
```

En el último caso, el tipo de resultado es [`BigInt`](@ref) ya que `BigInt` es el único tipo lo suficientemente grande como para contener enteros para aritmética de enteros de precisión arbitraria. También cabe señalar que no es necesario definir tanto `promote_rule(::Type{A}, ::Type{B})` como `promote_rule(::Type{B}, ::Type{A})` – la simetría se implica por la forma en que se utiliza `promote_rule` en el proceso de promoción.

La función `promote_rule` se utiliza como un bloque de construcción para definir una segunda función llamada [`promote_type`](@ref), que, dado cualquier número de objetos de tipo, devuelve el tipo común al que esos valores, como argumentos de `promote`, deberían ser promovidos. Así, si uno quiere saber, en ausencia de valores reales, a qué tipo se promovería una colección de valores de ciertos tipos, se puede usar `promote_type`:

```jldoctest
julia> promote_type(Int8, Int64)
Int64
```

Tenga en cuenta que **no** sobrecargamos `promote_type` directamente: sobrecargamos `promote_rule` en su lugar. `promote_type` utiliza `promote_rule` y añade la simetría. Sobrecargarlo directamente puede causar errores de ambigüedad. Sobrecargamos `promote_rule` para definir cómo deben ser promovidas las cosas, y usamos `promote_type` para consultar eso.

Internamente, `promote_type` se utiliza dentro de `promote` para determinar a qué tipo deben convertirse los valores de argumento para la promoción. El lector curioso puede leer el código en [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl), que define el mecanismo de promoción completo en unas 35 líneas.

### Case Study: Rational Promotions

Finalmente, concluimos nuestro estudio de caso en curso sobre el tipo de número racional de Julia, que hace un uso relativamente sofisticado del mecanismo de promoción con las siguientes reglas de promoción:

```julia
import Base: promote_rule
promote_rule(::Type{Rational{T}}, ::Type{S}) where {T<:Integer,S<:Integer} = Rational{promote_type(T,S)}
promote_rule(::Type{Rational{T}}, ::Type{Rational{S}}) where {T<:Integer,S<:Integer} = Rational{promote_type(T,S)}
promote_rule(::Type{Rational{T}}, ::Type{S}) where {T<:Integer,S<:AbstractFloat} = promote_type(T,S)
```

La primera regla dice que promover un número racional con cualquier otro tipo de entero se promueve a un tipo racional cuyo tipo de numerador/denominador es el resultado de la promoción de su tipo de numerador/denominador con el otro tipo de entero. La segunda regla aplica la misma lógica a dos tipos diferentes de números racionales, resultando en un racional de la promoción de sus respectivos tipos de numerador/denominador. La tercera y última regla dicta que promover un racional con un flotante resulta en el mismo tipo que promover el tipo de numerador/denominador con el flotante.

Este pequeño conjunto de reglas de promoción, junto con los constructores del tipo y el método `convert` predeterminado para números, son suficientes para hacer que los números racionales interoperen de manera completamente natural con todos los otros tipos numéricos de Julia: enteros, números de punto flotante y números complejos. Al proporcionar métodos de conversión apropiados y reglas de promoción de la misma manera, cualquier tipo numérico definido por el usuario puede interoparar de manera tan natural con los numéricos predefinidos de Julia.
