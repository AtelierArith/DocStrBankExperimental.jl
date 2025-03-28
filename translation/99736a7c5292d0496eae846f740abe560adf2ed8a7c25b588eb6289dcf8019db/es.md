# [Types](@id man-types)

Los sistemas de tipos tradicionalmente han caído en dos campos bastante diferentes: sistemas de tipos estáticos, donde cada expresión de programa debe tener un tipo computable antes de la ejecución del programa, y sistemas de tipos dinámicos, donde no se conoce nada sobre los tipos hasta el tiempo de ejecución, cuando los valores reales manipulados por el programa están disponibles. La orientación a objetos permite cierta flexibilidad en los lenguajes de tipo estático al permitir que el código se escriba sin que se conozcan los tipos precisos de los valores en el tiempo de compilación. La capacidad de escribir código que puede operar en diferentes tipos se llama polimorfismo. Todo el código en lenguajes dinámicamente tipados clásicos es polimórfico: solo al verificar explícitamente los tipos, o cuando los objetos no pueden soportar operaciones en tiempo de ejecución, se restringen los tipos de cualquier valor.

El sistema de tipos de Julia es dinámico, pero obtiene algunas de las ventajas de los sistemas de tipos estáticos al hacer posible indicar que ciertos valores son de tipos específicos. Esto puede ser de gran ayuda para generar código eficiente, pero aún más significativamente, permite que la selección de métodos en función de los tipos de los argumentos de las funciones esté profundamente integrada con el lenguaje. La selección de métodos se explora en detalle en [Methods](@ref), pero está arraigada en el sistema de tipos presentado aquí.

El comportamiento predeterminado en Julia cuando se omiten los tipos es permitir que los valores sean de cualquier tipo. Así, se pueden escribir muchas funciones útiles en Julia sin necesidad de usar tipos de manera explícita. Sin embargo, cuando se necesita una mayor expresividad, es fácil introducir gradualmente anotaciones de tipo explícitas en código previamente "sin tipo". Agregar anotaciones cumple tres propósitos principales: aprovechar el poderoso mecanismo de despacho múltiple de Julia, mejorar la legibilidad humana y detectar errores de programación.

Describiendo a Julia en la jerga de [type systems](https://en.wikipedia.org/wiki/Type_system), es: dinámica, nominativa y paramétrica. Los tipos genéricos pueden ser parametrizados, y las relaciones jerárquicas entre tipos son [explicitly declared](https://en.wikipedia.org/wiki/Nominal_type_system), en lugar de [implied by compatible structure](https://en.wikipedia.org/wiki/Structural_type_system). Una característica particularmente distintiva del sistema de tipos de Julia es que los tipos concretos no pueden ser subtipos entre sí: todos los tipos concretos son finales y solo pueden tener tipos abstractos como sus supertipos. Aunque esto puede parecer inicialmente demasiado restrictivo, tiene muchas consecuencias beneficiosas con sorprendentemente pocos inconvenientes. Resulta que poder heredar comportamiento es mucho más importante que poder heredar estructura, y heredar ambos causa dificultades significativas en lenguajes orientados a objetos tradicionales. Otros aspectos de alto nivel del sistema de tipos de Julia que deben mencionarse desde el principio son:

  * No hay división entre valores de objeto y no objeto: todos los valores en Julia son verdaderos objetos que tienen un tipo que pertenece a un único gráfico de tipos completamente conectado, todos los nodos de los cuales son igualmente de primera clase como tipos.
  * No hay un concepto significativo de un "tipo en tiempo de compilación": el único tipo que tiene un valor es su tipo real cuando el programa se está ejecutando. Esto se llama "tipo en tiempo de ejecución" en lenguajes orientados a objetos donde la combinación de la compilación estática con el polimorfismo hace que esta distinción sea significativa.
  * Solo los valores, no las variables, tienen tipos; las variables son simplemente nombres vinculados a valores, aunque por simplicidad podemos decir "tipo de una variable" como una forma abreviada de "tipo del valor al que se refiere una variable".
  * Tanto los tipos abstractos como los concretos pueden ser parametrizados por otros tipos. También pueden ser parametrizados por símbolos, por valores de cualquier tipo para el cual [`isbits`](@ref) devuelve verdadero (esencialmente, cosas como números y booleanos que se almacenan como tipos de C o `struct`s sin punteros a otros objetos), y también por tuplas de estos. Los parámetros de tipo pueden ser omitidos cuando no necesitan ser referenciados o restringidos.

El sistema de tipos de Julia está diseñado para ser poderoso y expresivo, pero a la vez claro, intuitivo y poco intrusivo. Muchos programadores de Julia pueden nunca sentir la necesidad de escribir código que utilice tipos de manera explícita. Sin embargo, algunos tipos de programación se vuelven más claros, simples, rápidos y robustos con tipos declarados.

## Type Declarations

El operador `::` se puede utilizar para adjuntar anotaciones de tipo a expresiones y variables en programas. Hay dos razones principales para hacer esto:

1. Como una afirmación para ayudar a confirmar que tu programa funciona como esperas, y
2. Para proporcionar información de tipo adicional al compilador, lo que puede mejorar el rendimiento en algunos casos.

Cuando se añade a una expresión que calcula un valor, el operador `::` se lee como "es una instancia de". Se puede usar en cualquier lugar para afirmar que el valor de la expresión a la izquierda es una instancia del tipo a la derecha. Cuando el tipo a la derecha es concreto, el valor a la izquierda debe tener ese tipo como su implementación; recuerda que todos los tipos concretos son finales, por lo que ninguna implementación es un subtipo de otra. Cuando el tipo es abstracto, es suficiente que el valor esté implementado por un tipo concreto que sea un subtipo del tipo abstracto. Si la afirmación de tipo no es verdadera, se lanza una excepción; de lo contrario, se devuelve el valor de la izquierda:

```jldoctest
julia> (1+2)::AbstractFloat
ERROR: TypeError: in typeassert, expected AbstractFloat, got a value of type Int64

julia> (1+2)::Int
3
```

Esto permite que una aserción de tipo se adjunte a cualquier expresión en su lugar.

Cuando se agrega a una variable en el lado izquierdo de una asignación, o como parte de una declaración `local`, el operador `::` significa algo un poco diferente: declara que la variable siempre tendrá el tipo especificado, como una declaración de tipo en un lenguaje de tipo estático como C. Cada valor asignado a la variable se convertirá al tipo declarado utilizando [`convert`](@ref):

```jldoctest
julia> function foo()
           x::Int8 = 100
           x
       end
foo (generic function with 1 method)

julia> x = foo()
100

julia> typeof(x)
Int8
```

Esta función es útil para evitar "sorpresas" de rendimiento que podrían ocurrir si una de las asignaciones a una variable cambiara su tipo inesperadamente.

Este comportamiento de "declaración" solo ocurre en contextos específicos:

```julia
local x::Int8  # in a local declaration
x::Int8 = 10   # as the left-hand side of an assignment
```

y se aplica a todo el ámbito actual, incluso antes de la declaración.

A partir de Julia 1.8, las declaraciones de tipo ahora se pueden usar en el ámbito global, es decir, se pueden agregar anotaciones de tipo a las variables globales para hacer que su acceso sea estable en cuanto al tipo.

```julia
julia> x::Int = 10
10

julia> x = 3.5
ERROR: InexactError: Int64(3.5)

julia> function foo(y)
           global x = 15.8    # throws an error when foo is called
           return x + y
       end
foo (generic function with 1 method)

julia> foo(10)
ERROR: InexactError: Int64(15.8)
```

Las declaraciones también se pueden adjuntar a las definiciones de funciones:

```julia
function sinc(x)::Float64
    if x == 0
        return 1
    end
    return sin(pi*x)/(pi*x)
end
```

El retorno de esta función se comporta igual que una asignación a una variable con un tipo declarado: el valor siempre se convierte a `Float64`.

## [Abstract Types](@id man-abstract-types)

Los tipos abstractos no pueden ser instanciados y sirven solo como nodos en el gráfico de tipos, describiendo así conjuntos de tipos concretos relacionados: aquellos tipos concretos que son sus descendientes. Comenzamos con tipos abstractos a pesar de que no tienen instanciación porque son la columna vertebral del sistema de tipos: forman la jerarquía conceptual que hace que el sistema de tipos de Julia sea más que solo una colección de implementaciones de objetos.

Recuerda que en [Integers and Floating-Point Numbers](@ref), introdujimos una variedad de tipos concretos de valores numéricos: [`Int8`](@ref), [`UInt8`](@ref), [`Int16`](@ref), [`UInt16`](@ref), [`Int32`](@ref), [`UInt32`](@ref), [`Int64`](@ref), [`UInt64`](@ref), [`Int128`](@ref), [`UInt128`](@ref), [`Float16`](@ref), [`Float32`](@ref), y [`Float64`](@ref). Aunque tienen diferentes tamaños de representación, `Int8`, `Int16`, `Int32`, `Int64` e `Int128` tienen en común que son tipos de enteros con signo. Del mismo modo, `UInt8`, `UInt16`, `UInt32`, `UInt64` y `UInt128` son todos tipos de enteros sin signo, mientras que `Float16`, `Float32` y `Float64` son distintos al ser tipos de punto flotante en lugar de enteros. Es común que un fragmento de código tenga sentido, por ejemplo, solo si sus argumentos son algún tipo de entero, pero no dependa realmente de qué *tipo* particular de entero. Por ejemplo, el algoritmo del máximo común divisor funciona para todos los tipos de enteros, pero no funcionará para números de punto flotante. Los tipos abstractos permiten la construcción de una jerarquía de tipos, proporcionando un contexto en el que los tipos concretos pueden encajar. Esto te permite, por ejemplo, programar fácilmente para cualquier tipo que sea un entero, sin restringir un algoritmo a un tipo específico de entero.

Los tipos abstractos se declaran utilizando la palabra clave [`abstract type`](@ref). Las sintaxis generales para declarar un tipo abstracto son:

```
abstract type «name» end
abstract type «name» <: «supertype» end
```

La palabra clave `abstract type` introduce un nuevo tipo abstracto, cuyo nombre se da por `«name»`. Este nombre puede ir opcionalmente seguido de [`<:`](@ref) y un tipo ya existente, indicando que el nuevo tipo abstracto declarado es un subtipo de este tipo "padre".

Cuando no se proporciona un supertipo, el supertipo predeterminado es `Any` – un tipo abstracto predefinido del que todos los objetos son instancias y todos los tipos son subtipos. En teoría de tipos, `Any` se llama comúnmente "top" porque está en la cúspide del gráfico de tipos. Julia también tiene un tipo abstracto "bottom" predefinido, en el nadir del gráfico de tipos, que se escribe como `Union{}`. Es exactamente lo opuesto de `Any`: ningún objeto es una instancia de `Union{}` y todos los tipos son supertypos de `Union{}`.

Consideremos algunos de los tipos abstractos que componen la jerarquía numérica de Julia:

```julia
abstract type Number end
abstract type Real          <: Number end
abstract type AbstractFloat <: Real end
abstract type Integer       <: Real end
abstract type Signed        <: Integer end
abstract type Unsigned      <: Integer end
```

El tipo [`Number`](@ref) es un tipo hijo directo de `Any`, y [`Real`](@ref) es su hijo. A su vez, `Real` tiene dos hijos (tiene más, pero solo se muestran dos aquí; llegaremos a los otros más tarde): [`Integer`](@ref) y [`AbstractFloat`](@ref), separando el mundo en representaciones de enteros y representaciones de números reales. Las representaciones de números reales incluyen tipos de punto flotante, pero también incluyen otros tipos, como los racionales. `AbstractFloat` incluye solo representaciones de punto flotante de números reales. Los enteros se subdividen aún más en variedades [`Signed`](@ref) y [`Unsigned`](@ref).

El operador `<:` en general significa "es un subtipo de", y, utilizado en declaraciones como las anteriores, declara que el tipo de la derecha es un supertipo inmediato del tipo recién declarado. También se puede usar en expresiones como un operador de subtipo que devuelve `true` cuando su operando izquierdo es un subtipo de su operando derecho:

```jldoctest
julia> Integer <: Number
true

julia> Integer <: AbstractFloat
false
```

Un uso importante de los tipos abstractos es proporcionar implementaciones predeterminadas para tipos concretos. Para dar un ejemplo simple, considere:

```julia
function myplus(x,y)
    x+y
end
```

Lo primero que hay que notar es que las declaraciones de argumentos anteriores son equivalentes a `x::Any` y `y::Any`. Cuando esta función se invoca, digamos como `myplus(2,5)`, el despachador elige el método más específico llamado `myplus` que coincide con los argumentos dados. (Consulta [Methods](@ref) para más información sobre el despacho múltiple.)

Suponiendo que no se encuentra un método más específico que el anterior, Julia define y compila internamente un método llamado `myplus` específicamente para dos argumentos `Int` basado en la función genérica dada arriba, es decir, define y compila implícitamente:

```julia
function myplus(x::Int,y::Int)
    x+y
end
```

y finalmente, invoca este método específico.

Así, los tipos abstractos permiten a los programadores escribir funciones genéricas que pueden ser utilizadas más tarde como el método predeterminado por muchas combinaciones de tipos concretos. Gracias al despacho múltiple, el programador tiene control total sobre si se utiliza el método predeterminado o uno más específico.

Un punto importante a tener en cuenta es que no hay pérdida de rendimiento si el programador confía en una función cuyos argumentos son tipos abstractos, porque se recompila para cada tupla de tipos de argumento concretos con los que se invoca. (Sin embargo, puede haber un problema de rendimiento en el caso de argumentos de función que son contenedores de tipos abstractos; consulte [Performance Tips](@ref man-performance-abstract-container).)

## Primitive Types

!!! warning
    Casi siempre es preferible envolver un tipo primitivo existente en un nuevo tipo compuesto que definir tu propio tipo primitivo.

    Esta funcionalidad existe para permitir que Julia inicie los tipos primitivos estándar que LLVM soporta. Una vez que están definidos, hay muy pocas razones para definir más.


Un tipo primitivo es un tipo concreto cuyos datos consisten en bits simples. Ejemplos clásicos de tipos primitivos son los enteros y los valores de punto flotante. A diferencia de la mayoría de los lenguajes, Julia te permite declarar tus propios tipos primitivos, en lugar de proporcionar solo un conjunto fijo de tipos incorporados. De hecho, los tipos primitivos estándar están todos definidos en el propio lenguaje:

```julia
primitive type Float16 <: AbstractFloat 16 end
primitive type Float32 <: AbstractFloat 32 end
primitive type Float64 <: AbstractFloat 64 end

primitive type Bool <: Integer 8 end
primitive type Char <: AbstractChar 32 end

primitive type Int8    <: Signed   8 end
primitive type UInt8   <: Unsigned 8 end
primitive type Int16   <: Signed   16 end
primitive type UInt16  <: Unsigned 16 end
primitive type Int32   <: Signed   32 end
primitive type UInt32  <: Unsigned 32 end
primitive type Int64   <: Signed   64 end
primitive type UInt64  <: Unsigned 64 end
primitive type Int128  <: Signed   128 end
primitive type UInt128 <: Unsigned 128 end
```

Las sintaxis generales para declarar un tipo primitivo son:

```
primitive type «name» «bits» end
primitive type «name» <: «supertype» «bits» end
```

El número de bits indica cuánto almacenamiento requiere el tipo y el nombre le da un nombre al nuevo tipo. Un tipo primitivo puede declararse opcionalmente como un subtipo de algún supertipo. Si se omite un supertipo, entonces el tipo por defecto tiene `Any` como su supertipo inmediato. La declaración de [`Bool`](@ref) anterior significa que un valor booleano ocupa ocho bits para almacenarse, y tiene [`Integer`](@ref) como su supertipo inmediato. Actualmente, solo se admiten tamaños que son múltiplos de 8 bits y es probable que experimentes errores de LLVM con tamaños diferentes a los utilizados anteriormente. Por lo tanto, los valores booleanos, aunque realmente solo necesitan un solo bit, no pueden declararse como más pequeños que ocho bits.

Los tipos [`Bool`](@ref), [`Int8`](@ref) y [`UInt8`](@ref) tienen representaciones idénticas: son fragmentos de memoria de ocho bits. Sin embargo, dado que el sistema de tipos de Julia es nominativo, no son intercambiables a pesar de tener una estructura idéntica. Una diferencia fundamental entre ellos es que tienen supertipos diferentes: el supertipo directo de `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566` es [`Integer`](@ref), el de `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` es [`Signed`](@ref), y el de `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566` es [`Unsigned`](@ref). Todas las demás diferencias entre `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566`, `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` y `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566` son cuestiones de comportamiento: la forma en que se definen las funciones para actuar cuando se les dan objetos de estos tipos como argumentos. Por eso es necesario un sistema de tipos nominativo: si la estructura determinara el tipo, que a su vez dicta el comportamiento, entonces sería imposible hacer que `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566` se comportara de manera diferente a `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` o `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566`.

## Composite Types

[Composite types](https://en.wikipedia.org/wiki/Composite_data_type) se llaman registros, estructuras u objetos en varios lenguajes. Un tipo compuesto es una colección de campos nombrados, una instancia de la cual puede ser tratada como un solo valor. En muchos lenguajes, los tipos compuestos son el único tipo definible por el usuario, y son, con mucho, el tipo definido por el usuario más comúnmente utilizado en Julia también.

En lenguajes de programación orientados a objetos convencionales, como C++, Java, Python y Ruby, los tipos compuestos también tienen funciones nombradas asociadas a ellos, y la combinación se llama "objeto". En lenguajes de programación orientados a objetos más puros, como Ruby o Smalltalk, todos los valores son objetos, ya sean compuestos o no. En lenguajes de programación orientados a objetos menos puros, incluidos C++ y Java, algunos valores, como enteros y valores de punto flotante, no son objetos, mientras que las instancias de tipos compuestos definidos por el usuario son verdaderos objetos con métodos asociados. En Julia, todos los valores son objetos, pero las funciones no están agrupadas con los objetos sobre los que operan. Esto es necesario ya que Julia elige qué método de una función usar mediante despacho múltiple, lo que significa que se consideran los tipos de *todos* los argumentos de una función al seleccionar un método, en lugar de solo el primero (ver [Methods](@ref) para más información sobre métodos y despacho). Por lo tanto, sería inapropiado que las funciones "pertenecieran" solo a su primer argumento. Organizar métodos en objetos de función en lugar de tener bolsas de métodos nombrados "dentro" de cada objeto resulta ser un aspecto altamente beneficioso del diseño del lenguaje.

Los tipos compuestos se introducen con la palabra clave [`struct`](@ref) seguida de un bloque de nombres de campo, opcionalmente anotados con tipos utilizando el operador `::`:

```jldoctest footype
julia> struct Foo
           bar
           baz::Int
           qux::Float64
       end
```

Los campos sin anotación de tipo se definen por defecto como `Any`, y por lo tanto pueden contener cualquier tipo de valor.

Se crean nuevos objetos del tipo `Foo` aplicando el objeto de tipo `Foo` como una función a los valores de sus campos:

```jldoctest footype
julia> foo = Foo("Hello, world.", 23, 1.5)
Foo("Hello, world.", 23, 1.5)

julia> typeof(foo)
Foo
```

Cuando un tipo se aplica como una función, se llama *constructor*. Se generan automáticamente dos constructores (estos se llaman *constructores predeterminados*). Uno acepta cualquier argumento y llama a [`convert`](@ref) para convertirlos a los tipos de los campos, y el otro acepta argumentos que coinciden exactamente con los tipos de los campos. La razón por la que se generan ambos es que esto facilita la adición de nuevas definiciones sin reemplazar inadvertidamente un constructor predeterminado.

Dado que el campo `bar` no tiene restricciones de tipo, cualquier valor servirá. Sin embargo, el valor de `baz` debe ser convertible a `Int`:

```jldoctest footype
julia> Foo((), 23.5, 1)
ERROR: InexactError: Int64(23.5)
Stacktrace:
[...]
```

Puede encontrar una lista de nombres de campo utilizando la función [`fieldnames`](@ref).

```jldoctest footype
julia> fieldnames(Foo)
(:bar, :baz, :qux)
```

Puedes acceder a los valores de campo de un objeto compuesto utilizando la notación tradicional `foo.bar`:

```jldoctest footype
julia> foo.bar
"Hello, world."

julia> foo.baz
23

julia> foo.qux
1.5
```

Los objetos compuestos declarados con `struct` son *inmutables*; no se pueden modificar después de la construcción. Esto puede parecer extraño al principio, pero tiene varias ventajas:

  * Puede ser más eficiente. Algunas estructuras se pueden empaquetar de manera eficiente en arreglos, y en algunos casos el compilador puede evitar la asignación de objetos inmutables por completo.
  * No es posible violar los invariantes proporcionados por los constructores del tipo.
  * El código que utiliza objetos inmutables puede ser más fácil de razonar.

Un objeto inmutable puede contener objetos mutables, como arreglos, como campos. Esos objetos contenidos seguirán siendo mutables; solo los campos del objeto inmutable en sí no se pueden cambiar para apuntar a diferentes objetos.

Donde sea necesario, los objetos compuestos mutables pueden ser declarados con la palabra clave [`mutable struct`](@ref), que se discutirá en la siguiente sección.

Si todos los campos de una estructura inmutable son indistinguibles (`===`), entonces dos valores inmutables que contienen esos campos también son indistinguibles:

```jldoctest
julia> struct X
           a::Int
           b::Float64
       end

julia> X(1, 2) === X(1, 2)
true
```

Hay mucho más que decir sobre cómo se crean las instancias de tipos compuestos, pero esa discusión depende tanto de [Parametric Types](@ref) como de [Methods](@ref), y es lo suficientemente importante como para ser abordada en su propia sección: [Constructors](@ref man-constructors).

Para muchos tipos definidos por el usuario `X`, es posible que desees definir un método [`Base.broadcastable(x::X) = Ref(x)`](@ref man-interfaces-broadcasting) para que las instancias de ese tipo actúen como "escalars" de 0 dimensiones para [broadcasting](@ref Broadcasting).

## Mutable Composite Types

Si un tipo compuesto se declara con `mutable struct` en lugar de `struct`, entonces las instancias de este pueden ser modificadas:

```jldoctest bartype
julia> mutable struct Bar
           baz
           qux::Float64
       end

julia> bar = Bar("Hello", 1.5);

julia> bar.qux = 2.0
2.0

julia> bar.baz = 1//2
1//2
```

Una interfaz adicional entre los campos y el usuario se puede proporcionar a través de [Instance Properties](@ref man-instance-properties). Esto otorga más control sobre lo que se puede acceder y modificar utilizando la notación `bar.baz`.

Para soportar la mutación, tales objetos generalmente se asignan en el heap y tienen direcciones de memoria estables. Un objeto mutable es como un pequeño contenedor que puede contener diferentes valores a lo largo del tiempo, y por lo tanto solo se puede identificar de manera confiable con su dirección. En contraste, una instancia de un tipo inmutable está asociada con valores de campo específicos; los valores de campo por sí solos te dicen todo sobre el objeto. Al decidir si hacer un tipo mutable, pregúntate si dos instancias con los mismos valores de campo se considerarían idénticas, o si podrían necesitar cambiar de manera independiente a lo largo del tiempo. Si se considerarían idénticas, el tipo probablemente debería ser inmutable.

Para resumir, dos propiedades esenciales definen la inmutabilidad en Julia:

  * No se permite modificar el valor de un tipo inmutable.

      * Para los tipos de bits, esto significa que el patrón de bits de un valor una vez establecido nunca cambiará y que ese valor es la identidad de un tipo de bits.
      * Para los tipos compuestos, esto significa que la identidad de los valores de sus campos nunca cambiará. Cuando los campos son tipos de bits, eso significa que sus bits nunca cambiarán; para los campos cuyos valores son tipos mutables como los arreglos, eso significa que los campos siempre se referirán al mismo valor mutable, aunque el contenido de ese valor mutable pueda ser modificado.
  * Un objeto con un tipo inmutable puede ser copiado libremente por el compilador, ya que su inmutabilidad hace imposible distinguir programáticamente entre el objeto original y una copia.

      * En particular, esto significa que los valores inmutables lo suficientemente pequeños, como enteros y flotantes, se pasan típicamente a las funciones en registros (o asignados en la pila).
      * Los valores mutables, por otro lado, se asignan en el heap y se pasan a las funciones como punteros a valores asignados en el heap, excepto en los casos en que el compilador está seguro de que no hay forma de saber que esto no es lo que está sucediendo.

En los casos en que uno o más campos de una estructura mutable, de otro modo, se sabe que son inmutables, se pueden declarar estos campos como tales utilizando `const`, como se muestra a continuación. Esto permite algunas, pero no todas, las optimizaciones de las estructuras inmutables, y se puede utilizar para hacer cumplir invariantes en los campos particulares marcados como `const`.

!!! compat "Julia 1.8"
    `const` anotar campos de estructuras mutables requiere al menos Julia 1.8.


```jldoctest baztype
julia> mutable struct Baz
           a::Int
           const b::Float64
       end

julia> baz = Baz(1, 1.5);

julia> baz.a = 2
2

julia> baz.b = 2.0
ERROR: setfield!: const field .b of type Baz cannot be changed
[...]
```

## [Declared Types](@id man-declared-types)

Los tres tipos de tipos (abstracto, primitivo, compuesto) discutidos en las secciones anteriores están en realidad todos estrechamente relacionados. Comparten las mismas propiedades clave:

  * Están explícitamente declarados.
  * Tienen nombres.
  * Han declarado explícitamente los supertipos.
  * Pueden tener parámetros.

Debido a estas propiedades compartidas, estos tipos se representan internamente como instancias del mismo concepto, `DataType`, que es el tipo de cualquiera de estos tipos:

```jldoctest
julia> typeof(Real)
DataType

julia> typeof(Int)
DataType
```

Un `DataType` puede ser abstracto o concreto. Si es concreto, tiene un tamaño especificado, un diseño de almacenamiento y (opcionalmente) nombres de campo. Así, un tipo primitivo es un `DataType` con tamaño distinto de cero, pero sin nombres de campo. Un tipo compuesto es un `DataType` que tiene nombres de campo o está vacío (tamaño cero).

Cada valor concreto en el sistema es una instancia de algún `DataType`.

## Type Unions

Una unión de tipos es un tipo abstracto especial que incluye como objetos todas las instancias de cualquiera de sus tipos de argumento, construidas utilizando la palabra clave especial [`Union`](@ref):

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 :: IntOrString
1

julia> "Hello!" :: IntOrString
"Hello!"

julia> 1.0 :: IntOrString
ERROR: TypeError: in typeassert, expected Union{Int64, AbstractString}, got a value of type Float64
```

Los compiladores de muchos lenguajes tienen una construcción de unión interna para razonar sobre tipos; Julia simplemente la expone al programador. El compilador de Julia es capaz de generar código eficiente en presencia de tipos `Union` con un pequeño número de tipos [^1], generando código especializado en ramas separadas para cada tipo posible.

Un caso particularmente útil de un tipo `Union` es `Union{T, Nothing}`, donde `T` puede ser cualquier tipo y [`Nothing`](@ref) es el tipo singleton cuya única instancia es el objeto [`nothing`](@ref). Este patrón es el equivalente en Julia de los tipos [`Nullable`, `Option` or `Maybe`](https://en.wikipedia.org/wiki/Nullable_type) en otros lenguajes. Declarar un argumento de función o un campo como `Union{T, Nothing}` permite establecerlo ya sea a un valor del tipo `T`, o a `nothing` para indicar que no hay valor. Consulte [this FAQ entry](@ref faq-nothing) para más información.

## Parametric Types

Una característica importante y poderosa del sistema de tipos de Julia es que es paramétrico: los tipos pueden tomar parámetros, de modo que las declaraciones de tipos en realidad introducen toda una familia de nuevos tipos, uno para cada combinación posible de valores de parámetros. Hay muchos lenguajes que soportan alguna versión de [generic programming](https://en.wikipedia.org/wiki/Generic_programming), en los que las estructuras de datos y los algoritmos para manipularlas pueden ser especificados sin especificar los tipos exactos involucrados. Por ejemplo, alguna forma de programación genérica existe en ML, Haskell, Ada, Eiffel, C++, Java, C#, F# y Scala, solo por nombrar algunos. Algunos de estos lenguajes soportan verdadero polimorfismo paramétrico (por ejemplo, ML, Haskell, Scala), mientras que otros soportan estilos de programación genérica ad-hoc, basados en plantillas (por ejemplo, C++, Java). Con tantas variedades diferentes de programación genérica y tipos paramétricos en varios lenguajes, no intentaremos comparar los tipos paramétricos de Julia con otros lenguajes, sino que nos centraremos en explicar el sistema de Julia por derecho propio. Sin embargo, notaremos que, dado que Julia es un lenguaje de tipado dinámico y no necesita tomar todas las decisiones de tipo en tiempo de compilación, muchas de las dificultades tradicionales encontradas en sistemas de tipos paramétricos estáticos pueden ser manejadas relativamente fácilmente.

Todos los tipos declarados (la variedad `DataType`) pueden ser parametrizados, con la misma sintaxis en cada caso. Los discutiremos en el siguiente orden: primero, tipos compuestos paramétricos, luego, tipos abstractos paramétricos y, finalmente, tipos primitivos paramétricos.

### [Parametric Composite Types](@id man-parametric-composite-types)

Los parámetros de tipo se introducen inmediatamente después del nombre del tipo, rodeados por llaves:

```jldoctest pointtype
julia> struct Point{T}
           x::T
           y::T
       end
```

Esta declaración define un nuevo tipo paramétrico, `Point{T}`, que contiene dos "coordenadas" del tipo `T`. ¿Qué es, se puede preguntar, `T`? Bueno, ese es precisamente el punto de los tipos paramétricos: puede ser cualquier tipo (o un valor de cualquier tipo de bits, de hecho, aunque aquí se usa claramente como un tipo). `Point{Float64}` es un tipo concreto equivalente al tipo definido al reemplazar `T` en la definición de `Point` con [`Float64`](@ref). Por lo tanto, esta única declaración en realidad declara un número ilimitado de tipos: `Point{Float64}`, `Point{AbstractString}`, `Point{Int64}`, etc. Cada uno de estos es ahora un tipo concreto utilizable:

```jldoctest pointtype
julia> Point{Float64}
Point{Float64}

julia> Point{AbstractString}
Point{AbstractString}
```

El tipo `Point{Float64}` es un punto cuyas coordenadas son valores de punto flotante de 64 bits, mientras que el tipo `Point{AbstractString}` es un "punto" cuyas "coordenadas" son objetos de cadena (ver [Strings](@ref)).

`Point` en sí mismo también es un objeto de tipo válido, que contiene todas las instancias `Point{Float64}`, `Point{AbstractString}`, etc. como subtipos:

```jldoctest pointtype
julia> Point{Float64} <: Point
true

julia> Point{AbstractString} <: Point
true
```

Otros tipos, por supuesto, no son subtipos de él:

```jldoctest pointtype
julia> Float64 <: Point
false

julia> AbstractString <: Point
false
```

Los tipos `Point` concretos con diferentes valores de `T` nunca son subtipos entre sí:

```jldoctest pointtype
julia> Point{Float64} <: Point{Int64}
false

julia> Point{Float64} <: Point{Real}
false
```

!!! warning
    Este último punto es *muy* importante: aunque `Float64 <: Real` **NO** tenemos `Point{Float64} <: Point{Real}`.


En otras palabras, en el lenguaje de la teoría de tipos, los parámetros de tipo de Julia son *invariantes*, en lugar de ser [covariant (or even contravariant)](https://en.wikipedia.org/wiki/Covariance_and_contravariance_%28computer_science%29). Esto es por razones prácticas: aunque cualquier instancia de `Point{Float64}` puede ser conceptualmente como una instancia de `Point{Real}` también, los dos tipos tienen diferentes representaciones en memoria:

  * Una instancia de `Point{Float64}` puede representarse de manera compacta y eficiente como un par inmediato de valores de 64 bits;
  * Una instancia de `Point{Real}` debe ser capaz de contener cualquier par de instancias de [`Real`](@ref). Dado que los objetos que son instancias de `Real` pueden ser de tamaño y estructura arbitrarios, en la práctica, una instancia de `Point{Real}` debe ser representada como un par de punteros a objetos `Real` asignados individualmente.

La eficiencia ganada al poder almacenar `Point{Float64}` objetos con valores inmediatos se magnifica enormemente en el caso de los arreglos: un `Array{Float64}` puede ser almacenado como un bloque de memoria contiguo de valores de punto flotante de 64 bits, mientras que un `Array{Real}` debe ser un arreglo de punteros a [`Real`](@ref) objetos asignados individualmente – que bien pueden ser [boxed](https://en.wikipedia.org/wiki/Object_type_%28object-oriented_programming%29#Boxing) valores de punto flotante de 64 bits, pero también podrían ser objetos complejos y arbitrariamente grandes, que se declaran como implementaciones del tipo abstracto `Real`.

Dado que `Point{Float64}` no es un subtipo de `Point{Real}`, el siguiente método no se puede aplicar a argumentos de tipo `Point{Float64}`:

```julia
function norm(p::Point{Real})
    sqrt(p.x^2 + p.y^2)
end
```

Una forma correcta de definir un método que acepte todos los argumentos del tipo `Point{T}` donde `T` es un subtipo de [`Real`](@ref) es:

```julia
function norm(p::Point{<:Real})
    sqrt(p.x^2 + p.y^2)
end
```

(Equivalente, se podría definir `function norm(p::Point{T} where T<:Real)` o `function norm(p::Point{T}) where T<:Real`; ver [UnionAll Types](@ref).)

Se discutirán más ejemplos más adelante en [Methods](@ref).

¿Cómo se construye un objeto `Point`? Es posible definir constructores personalizados para tipos compuestos, que se discutirán en detalle en [Constructors](@ref man-constructors), pero en ausencia de declaraciones de constructores especiales, hay dos formas predeterminadas de crear nuevos objetos compuestos, una en la que los parámetros de tipo se dan explícitamente y la otra en la que se implican por los argumentos del constructor del objeto.

Since the type `Point{Float64}` is a concrete type equivalent to `Point` declared with [`Float64`](@ref) in place of `T`, it can be applied as a constructor accordingly:

```jldoctest pointtype
julia> p = Point{Float64}(1.0, 2.0)
Point{Float64}(1.0, 2.0)

julia> typeof(p)
Point{Float64}
```

Para el constructor predeterminado, debe proporcionarse exactamente un argumento para cada campo:

```jldoctest pointtype
julia> Point{Float64}(1.0)
ERROR: MethodError: no method matching Point{Float64}(::Float64)
The type `Point{Float64}` exists, but no method is defined for this combination of argument types when trying to construct it.
[...]

julia> Point{Float64}(1.0, 2.0, 3.0)
ERROR: MethodError: no method matching Point{Float64}(::Float64, ::Float64, ::Float64)
The type `Point{Float64}` exists, but no method is defined for this combination of argument types when trying to construct it.
[...]
```

Solo se genera un constructor predeterminado para tipos paramétricos, ya que no es posible sobrescribirlo. Este constructor acepta cualquier argumento y los convierte a los tipos de campo.

En muchos casos, es redundante proporcionar el tipo de objeto `Point` que se desea construir, ya que los tipos de argumentos en la llamada al constructor ya proporcionan implícitamente información de tipo. Por esa razón, también puedes aplicar `Point` como un constructor, siempre que el valor implícito del tipo de parámetro `T` sea inequívoco:

```jldoctest pointtype
julia> p1 = Point(1.0,2.0)
Point{Float64}(1.0, 2.0)

julia> typeof(p1)
Point{Float64}

julia> p2 = Point(1,2)
Point{Int64}(1, 2)

julia> typeof(p2)
Point{Int64}
```

En el caso de `Point`, el tipo de `T` se implica de manera inequívoca si y solo si los dos argumentos de `Point` tienen el mismo tipo. Cuando este no es el caso, el constructor fallará con un [`MethodError`](@ref):

```jldoctest pointtype
julia> Point(1,2.5)
ERROR: MethodError: no method matching Point(::Int64, ::Float64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, !Matched::T) where T
   @ Main none:2

Stacktrace:
[...]
```

Se pueden definir métodos de constructor para manejar adecuadamente tales casos mixtos, pero eso no se discutirá hasta más adelante en [Constructors](@ref man-constructors).

### Parametric Abstract Types

Las declaraciones de tipos abstractos paramétricos declaran una colección de tipos abstractos, de manera muy similar:

```jldoctest pointytype
julia> abstract type Pointy{T} end
```

Con esta declaración, `Pointy{T}` es un tipo abstracto distinto para cada tipo o valor entero de `T`. Al igual que con los tipos compuestos paramétricos, cada instancia de este tipo es un subtipo de `Pointy`:

```jldoctest pointytype
julia> Pointy{Int64} <: Pointy
true

julia> Pointy{1} <: Pointy
true
```

Los tipos abstractos paramétricos son invariantes, al igual que los tipos compuestos paramétricos:

```jldoctest pointytype
julia> Pointy{Float64} <: Pointy{Real}
false

julia> Pointy{Real} <: Pointy{Float64}
false
```

La notación `Pointy{<:Real}` se puede usar para expresar el análogo de tipo *covariante* en Julia, mientras que `Pointy{>:Int}` representa el análogo de un tipo *contravariante*, pero técnicamente estos representan *conjuntos* de tipos (ver [UnionAll Types](@ref)).

```jldoctest pointytype
julia> Pointy{Float64} <: Pointy{<:Real}
true

julia> Pointy{Real} <: Pointy{>:Int}
true
```

Así como los tipos abstractos simples sirven para crear una jerarquía útil de tipos sobre tipos concretos, los tipos abstractos paramétricos cumplen el mismo propósito con respecto a los tipos compuestos paramétricos. Podríamos, por ejemplo, haber declarado `Point{T}` como un subtipo de `Pointy{T}` de la siguiente manera:

```jldoctest pointytype
julia> struct Point{T} <: Pointy{T}
           x::T
           y::T
       end
```

Dada tal declaración, para cada elección de `T`, tenemos `Point{T}` como un subtipo de `Pointy{T}`:

```jldoctest pointytype
julia> Point{Float64} <: Pointy{Float64}
true

julia> Point{Real} <: Pointy{Real}
true

julia> Point{AbstractString} <: Pointy{AbstractString}
true
```

Esta relación también es invariante:

```jldoctest pointytype
julia> Point{Float64} <: Pointy{Real}
false

julia> Point{Float64} <: Pointy{<:Real}
true
```

Los tipos abstractos paramétricos como `Pointy` sirven para definir una interfaz o un comportamiento común que puede ser implementado por diferentes tipos de datos. Esto permite la creación de estructuras de datos y funciones que son más flexibles y reutilizables.

```jldoctest pointytype
julia> struct DiagPoint{T} <: Pointy{T}
           x::T
       end
```

Ahora tanto `Point{Float64}` como `DiagPoint{Float64}` son implementaciones de la abstracción `Pointy{Float64}`, y de manera similar para cada otra elección posible del tipo `T`. Esto permite programar a una interfaz común compartida por todos los objetos `Pointy`, implementada tanto para `Point` como para `DiagPoint`. Sin embargo, esto no se puede demostrar completamente hasta que hayamos introducido métodos y despacho en la siguiente sección, [Methods](@ref).

Hay situaciones en las que puede no tener sentido que los parámetros de tipo varíen libremente sobre todos los tipos posibles. En tales situaciones, se puede restringir el rango de `T` de la siguiente manera:

```jldoctest realpointytype
julia> abstract type Pointy{T<:Real} end
```

Con tal declaración, es aceptable usar cualquier tipo que sea un subtipo de [`Real`](@ref) en lugar de `T`, pero no tipos que no son subtipos de `Real`:

```jldoctest realpointytype
julia> Pointy{Float64}
Pointy{Float64}

julia> Pointy{Real}
Pointy{Real}

julia> Pointy{AbstractString}
ERROR: TypeError: in Pointy, in T, expected T<:Real, got Type{AbstractString}

julia> Pointy{1}
ERROR: TypeError: in Pointy, in T, expected T<:Real, got a value of type Int64
```

Los parámetros de tipo para tipos compuestos paramétricos pueden ser restringidos de la misma manera:

```julia
struct Point{T<:Real} <: Pointy{T}
    x::T
    y::T
end
```

Para dar un ejemplo del mundo real de cómo toda esta maquinaria de tipos paramétricos puede ser útil, aquí está la definición real del tipo inmutable [`Rational`](@ref) de Julia (excepto que omitimos el constructor aquí por simplicidad), que representa una relación exacta de enteros:

```julia
struct Rational{T<:Integer} <: Real
    num::T
    den::T
end
```

Solo tiene sentido tomar razones de valores enteros, por lo que el tipo de parámetro `T` se restringe a ser un subtipo de [`Integer`](@ref), y una razón de enteros representa un valor en la recta numérica real, por lo que cualquier [`Rational`](@ref) es una instancia de la abstracción [`Real`](@ref).

### Tuple Types

Las tuplas son una abstracción de los argumentos de una función, sin la función misma. Los aspectos más destacados de los argumentos de una función son su orden y sus tipos. Por lo tanto, un tipo de tupla es similar a un tipo inmutable parametrizado donde cada parámetro es el tipo de un campo. Por ejemplo, un tipo de tupla de 2 elementos se asemeja al siguiente tipo inmutable:

```julia
struct Tuple2{A,B}
    a::A
    b::B
end
```

Sin embargo, hay tres diferencias clave:

  * Los tipos de tuplas pueden tener cualquier número de parámetros.
  * Los tipos de tuplas son *covariantes* en sus parámetros: `Tuple{Int}` es un subtipo de `Tuple{Any}`. Por lo tanto, `Tuple{Any}` se considera un tipo abstracto, y los tipos de tuplas son concretos solo si sus parámetros lo son.
  * Las tuplas no tienen nombres de campo; los campos solo se acceden por índice.

Los valores de una tupla se escriben con paréntesis y comas. Cuando se construye una tupla, se genera un tipo de tupla apropiado bajo demanda:

```jldoctest
julia> typeof((1,"foo",2.5))
Tuple{Int64, String, Float64}
```

Nota las implicaciones de la covarianza:

```jldoctest
julia> Tuple{Int,AbstractString} <: Tuple{Real,Any}
true

julia> Tuple{Int,AbstractString} <: Tuple{Real,Real}
false

julia> Tuple{Int,AbstractString} <: Tuple{Real,}
false
```

Intuitivamente, esto corresponde a que el tipo de los argumentos de una función sea un subtipo de la firma de la función (cuando la firma coincide).

### Vararg Tuple Types

El último parámetro de un tipo de tupla puede ser el valor especial [`Vararg`](@ref), que denota cualquier número de elementos finales:

```jldoctest
julia> mytupletype = Tuple{AbstractString,Vararg{Int}}
Tuple{AbstractString, Vararg{Int64}}

julia> isa(("1",), mytupletype)
true

julia> isa(("1",1), mytupletype)
true

julia> isa(("1",1,2), mytupletype)
true

julia> isa(("1",1,2,3.0), mytupletype)
false
```

Además, `Vararg{T}` corresponde a cero o más elementos del tipo `T`. Los tipos de tupla Vararg se utilizan para representar los argumentos aceptados por los métodos varargs (ver [Varargs Functions](@ref)).

El valor especial `Vararg{T,N}` (cuando se usa como el último parámetro de un tipo de tupla) corresponde exactamente a `N` elementos del tipo `T`. `NTuple{N,T}` es un alias conveniente para `Tuple{Vararg{T,N}}`, es decir, un tipo de tupla que contiene exactamente `N` elementos del tipo `T`.

### Named Tuple Types

Las tuplas nombradas son instancias del tipo [`NamedTuple`](@ref), que tiene dos parámetros: una tupla de símbolos que da los nombres de los campos y un tipo de tupla que da los tipos de los campos. Para conveniencia, los tipos `NamedTuple` se imprimen utilizando el macro [`@NamedTuple`](@ref), que proporciona una sintaxis similar a `struct` conveniente para declarar estos tipos a través de declaraciones `key::Type`, donde un `::Type` omitido corresponde a `::Any`.

```jldoctest
julia> typeof((a=1,b="hello")) # prints in macro form
@NamedTuple{a::Int64, b::String}

julia> NamedTuple{(:a, :b), Tuple{Int64, String}} # long form of the type
@NamedTuple{a::Int64, b::String}
```

La forma `begin ... end` del macro `@NamedTuple` permite que las declaraciones se dividan en múltiples líneas (similar a una declaración de struct), pero es de otro modo equivalente:

```jldoctest
julia> @NamedTuple begin
           a::Int
           b::String
       end
@NamedTuple{a::Int64, b::String}
```

Un tipo `NamedTuple` se puede usar como un constructor, aceptando un único argumento de tupla. El tipo `NamedTuple` construido puede ser un tipo concreto, con ambos parámetros especificados, o un tipo que especifica solo los nombres de los campos:

```jldoctest
julia> @NamedTuple{a::Float32,b::String}((1, ""))
(a = 1.0f0, b = "")

julia> NamedTuple{(:a, :b)}((1, ""))
(a = 1, b = "")
```

Si se especifican tipos de campo, los argumentos se convierten. De lo contrario, se utilizan directamente los tipos de los argumentos.

### Parametric Primitive Types

Los tipos primitivos también se pueden declarar de manera paramétrica. Por ejemplo, los punteros se representan como tipos primitivos que se declararían en Julia de la siguiente manera:

```julia
# 32-bit system:
primitive type Ptr{T} 32 end

# 64-bit system:
primitive type Ptr{T} 64 end
```

La característica ligeramente extraña de estas declaraciones en comparación con los tipos compuestos paramétricos típicos, es que el parámetro de tipo `T` no se utiliza en la definición del tipo en sí; es solo una etiqueta abstracta, que define esencialmente toda una familia de tipos con una estructura idéntica, diferenciados solo por su parámetro de tipo. Así, `Ptr{Float64}` y `Ptr{Int64}` son tipos distintos, a pesar de que tienen representaciones idénticas. Y, por supuesto, todos los tipos de punteros específicos son subtipos del tipo paraguas [`Ptr`](@ref):

```jldoctest
julia> Ptr{Float64} <: Ptr
true

julia> Ptr{Int64} <: Ptr
true
```

## UnionAll Types

Hemos dicho que un tipo paramétrico como `Ptr` actúa como un supertipo de todas sus instancias (`Ptr{Int64}` etc.). ¿Cómo funciona esto? `Ptr` en sí mismo no puede ser un tipo de dato normal, ya que sin conocer el tipo de los datos referenciados, el tipo claramente no puede ser utilizado para operaciones de memoria. La respuesta es que `Ptr` (u otros tipos paramétricos como `Array`) es un tipo de tipo diferente llamado un tipo [`UnionAll`](@ref). Tal tipo expresa la *unión iterada* de tipos para todos los valores de algún parámetro.

Los tipos `UnionAll` generalmente se escriben utilizando la palabra clave `where`. Por ejemplo, `Ptr` podría escribirse de manera más precisa como `Ptr{T} where T`, lo que significa todos los valores cuyo tipo es `Ptr{T}` para algún valor de `T`. En este contexto, el parámetro `T` también se llama a menudo "variable de tipo" ya que es como una variable que abarca tipos. Cada `where` introduce una única variable de tipo, por lo que estas expresiones están anidadas para tipos con múltiples parámetros, por ejemplo, `Array{T,N} where N where T`.

La sintaxis de aplicación de tipo `A{B,C}` requiere que `A` sea un tipo `UnionAll`, y primero sustituye `B` por la variable de tipo más externa en `A`. Se espera que el resultado sea otro tipo `UnionAll`, en el que luego se sustituye `C`. Así, `A{B,C}` es equivalente a `A{B}{C}`. Esto explica por qué es posible instanciar parcialmente un tipo, como en `Array{Float64}`: el primer valor del parámetro ha sido fijado, pero el segundo aún abarca todos los valores posibles. Usando la sintaxis explícita `where`, se puede fijar cualquier subconjunto de parámetros. Por ejemplo, el tipo de todos los arreglos unidimensionales se puede escribir como `Array{T,1} where T`.

Las variables de tipo pueden ser restringidas con relaciones de subtipo. `Array{T} where T<:Integer` se refiere a todos los arreglos cuyo tipo de elemento es algún tipo de [`Integer`](@ref). La sintaxis `Array{<:Integer}` es una forma abreviada conveniente para `Array{T} where T<:Integer`. Las variables de tipo pueden tener tanto límites inferiores como superiores. `Array{T} where Int<:T<:Number` se refiere a todos los arreglos de [`Number`](@ref)s que pueden contener `Int`s (ya que `T` debe ser al menos tan grande como `Int`). La sintaxis `where T>:Int` también funciona para especificar solo el límite inferior de una variable de tipo, y `Array{>:Int}` es equivalente a `Array{T} where T>:Int`.

Dado que las expresiones `where` se anidan, los límites de las variables de tipo pueden referirse a variables de tipo externas. Por ejemplo, `Tuple{T,Array{S}} where S<:AbstractArray{T} where T<:Real` se refiere a tuplas de 2 elementos cuyo primer elemento es algún [`Real`](@ref), y cuyo segundo elemento es un `Array` de cualquier tipo de arreglo cuyo tipo de elemento contenga el tipo del primer elemento de la tupla.

La palabra clave `where` puede estar anidada dentro de una declaración más compleja. Por ejemplo, considere los dos tipos creados por las siguientes declaraciones:

```jldoctest
julia> const T1 = Array{Array{T, 1} where T, 1}
Vector{Vector} (alias for Array{Array{T, 1} where T, 1})

julia> const T2 = Array{Array{T, 1}, 1} where T
Array{Vector{T}, 1} where T
```

El tipo `T1` define un arreglo unidimensional de arreglos unidimensionales; cada uno de los arreglos internos consiste en objetos del mismo tipo, pero este tipo puede variar de un arreglo interno a otro. Por otro lado, el tipo `T2` define un arreglo unidimensional de arreglos unidimensionales todos cuyos arreglos internos deben tener el mismo tipo. Tenga en cuenta que `T2` es un tipo abstracto, por ejemplo, `Array{Array{Int,1},1} <: T2`, mientras que `T1` es un tipo concreto. Como consecuencia, `T1` se puede construir con un constructor sin argumentos `a=T1()`, pero `T2` no puede.

Hay una sintaxis conveniente para nombrar tales tipos, similar a la forma corta de la sintaxis de definición de funciones:

```julia
Vector{T} = Array{T, 1}
```

Esto es equivalente a `const Vector = Array{T,1} donde T`. Escribir `Vector{Float64}` es equivalente a escribir `Array{Float64,1}`, y el tipo paraguas `Vector` tiene como instancias todos los objetos `Array` donde el segundo parámetro – el número de dimensiones del array – es 1, independientemente de cuál sea el tipo de elemento. En lenguajes donde los tipos paramétricos deben especificarse siempre en su totalidad, esto no es especialmente útil, pero en Julia, esto permite escribir solo `Vector` para el tipo abstracto que incluye todos los arrays densos unidimensionales de cualquier tipo de elemento.

## [Singleton types](@id man-singleton-types)

Los tipos compuestos inmutables sin campos se llaman *singletons*. Formalmente, si

1. `T` es un tipo compuesto inmutable (es decir, definido con `struct`),
2. `a es T && b es T` implica `a === b`,

entonces `T` es un tipo singleton.[^2] [`Base.issingletontype`](@ref) se puede usar para verificar si un tipo es un tipo singleton. [Abstract types](@ref man-abstract-types) no puede ser tipos singleton por construcción.

De la definición, se deduce que solo puede haber una instancia de tales tipos:

```jldoctest
julia> struct NoFields
       end

julia> NoFields() === NoFields()
true

julia> Base.issingletontype(NoFields)
true
```

La función [`===`](@ref) confirma que las instancias construidas de `NoFields` son en realidad una y la misma.

Los tipos paramétricos pueden ser tipos singleton cuando se cumple la condición anterior. Por ejemplo,

```jldoctest
julia> struct NoFieldsParam{T}
       end

julia> Base.issingletontype(NoFieldsParam) # Can't be a singleton type ...
false

julia> NoFieldsParam{Int}() isa NoFieldsParam # ... because it has ...
true

julia> NoFieldsParam{Bool}() isa NoFieldsParam # ... multiple instances.
true

julia> Base.issingletontype(NoFieldsParam{Int}) # Parametrized, it is a singleton.
true

julia> NoFieldsParam{Int}() === NoFieldsParam{Int}()
true
```

## Types of functions

Cada función tiene su propio tipo, que es un subtipo de `Function`.

```jldoctest foo41
julia> foo41(x) = x + 1
foo41 (generic function with 1 method)

julia> typeof(foo41)
typeof(foo41) (singleton type of function foo41, subtype of Function)
```

Nota cómo `typeof(foo41)` se imprime como sí mismo. Esta es simplemente una convención para imprimir, ya que es un objeto de primera clase que se puede usar como cualquier otro valor:

```jldoctest foo41
julia> T = typeof(foo41)
typeof(foo41) (singleton type of function foo41, subtype of Function)

julia> T <: Function
true
```

Los tipos de funciones definidos en el nivel superior son singletons. Cuando sea necesario, puedes compararlos con [`===`](@ref).

[Closures](@ref man-anonymous-functions) también tienen su propio tipo, que generalmente se imprime con nombres que terminan en `#<número>`. Los nombres y tipos de funciones definidas en diferentes ubicaciones son distintos, pero no se garantiza que se impriman de la misma manera en diferentes sesiones.

```jldoctest; filter = r"[0-9\.]+"
julia> typeof(x -> x + 1)
var"#9#10"
```

Los tipos de cierres no son necesariamente singletons.

```jldoctest
julia> addy(y) = x -> x + y
addy (generic function with 1 method)

julia> typeof(addy(1)) === typeof(addy(2))
true

julia> addy(1) === addy(2)
false

julia> Base.issingletontype(typeof(addy(1)))
false
```

## [`Type{T}` type selectors](@id man-typet-type)

Para cada tipo `T`, `Type{T}` es un tipo paramétrico abstracto cuya única instancia es el objeto `T`. Hasta que discutamos [Parametric Methods](@ref) y [conversions](@ref conversion-and-promotion), es difícil explicar la utilidad de este constructo, pero en resumen, permite especializar el comportamiento de las funciones en tipos específicos como *valores*. Esto es útil para escribir métodos (especialmente paramétricos) cuyo comportamiento depende de un tipo que se da como un argumento explícito en lugar de ser implícito por el tipo de uno de sus argumentos.

Dado que la definición es un poco difícil de entender, veamos algunos ejemplos:

```jldoctest
julia> isa(Float64, Type{Float64})
true

julia> isa(Real, Type{Float64})
false

julia> isa(Real, Type{Real})
true

julia> isa(Float64, Type{Real})
false
```

En otras palabras, [`isa(A, Type{B})`](@ref) es verdadero si y solo si `A` y `B` son el mismo objeto y ese objeto es un tipo.

En particular, dado que los tipos paramétricos son [invariant](@ref man-parametric-composite-types), tenemos

```jldoctest
julia> struct TypeParamExample{T}
           x::T
       end

julia> TypeParamExample isa Type{TypeParamExample}
true

julia> TypeParamExample{Int} isa Type{TypeParamExample}
false

julia> TypeParamExample{Int} isa Type{TypeParamExample{Int}}
true
```

Sin el parámetro, `Type` es simplemente un tipo abstracto que tiene todos los objetos de tipo como sus instancias:

```jldoctest
julia> isa(Type{Float64}, Type)
true

julia> isa(Float64, Type)
true

julia> isa(Real, Type)
true
```

Cualquier objeto que no sea un tipo no es una instancia de `Type`:

```jldoctest
julia> isa(1, Type)
false

julia> isa("foo", Type)
false
```

Mientras que `Type` es parte de la jerarquía de tipos de Julia como cualquier otro tipo paramétrico abstracto, no se utiliza comúnmente fuera de las firmas de métodos, excepto en algunos casos especiales. Otro caso de uso importante para `Type` es el afinamiento de tipos de campo que de otro modo se capturarían de manera menos precisa, por ejemplo, como [`DataType`](@ref man-declared-types) en el ejemplo a continuación, donde el constructor predeterminado podría llevar a problemas de rendimiento en el código que depende del tipo envuelto preciso (de manera similar a [abstract type parameters](@ref man-performance-abstract-container)).

```jldoctest
julia> struct WrapType{T}
       value::T
       end

julia> WrapType(Float64) # default constructor, note DataType
WrapType{DataType}(Float64)

julia> WrapType(::Type{T}) where T = WrapType{Type{T}}(T)
WrapType

julia> WrapType(Float64) # sharpened constructor, note more precise Type{Float64}
WrapType{Type{Float64}}(Float64)
```

## Type Aliases

A veces es conveniente introducir un nuevo nombre para un tipo ya expresable. Esto se puede hacer con una simple declaración de asignación. Por ejemplo, `UInt` se alias a [`UInt32`](@ref) o [`UInt64`](@ref) según sea apropiado para el tamaño de los punteros en el sistema:

```julia-repl
# 32-bit system:
julia> UInt
UInt32

# 64-bit system:
julia> UInt
UInt64
```

Esto se logra a través del siguiente código en `base/boot.jl`:

```julia
if Int === Int64
    const UInt = UInt64
else
    const UInt = UInt32
end
```

Por supuesto, esto depende de a qué se le haya asignado el alias `Int` – pero eso está predefinido para ser el tipo correcto – ya sea [`Int32`](@ref) o [`Int64`](@ref).

(Tenga en cuenta que a diferencia de `Int`, `Float` no existe como un alias de tipo para un tamaño específico [`AbstractFloat`](@ref). A diferencia de los registros enteros, donde el tamaño de `Int` refleja el tamaño de un puntero nativo en esa máquina, los tamaños de los registros de punto flotante están especificados por el estándar IEEE-754.)

Los alias de tipo pueden ser parametrizados:

```jldoctest
julia> const Family{T} = Set{T}
Set

julia> Family{Char} === Set{Char}
true
```

## Operations on Types

Dado que los tipos en Julia son en sí mismos objetos, las funciones ordinarias pueden operar sobre ellos. Algunas funciones que son particularmente útiles para trabajar con o explorar tipos ya se han introducido, como el operador `<:`, que indica si su operando izquierdo es un subtipo de su operando derecho.

La función [`isa`](@ref) prueba si un objeto es de un tipo dado y devuelve verdadero o falso:

```jldoctest
julia> isa(1, Int)
true

julia> isa(1, AbstractFloat)
false
```

La función [`typeof`](@ref), ya utilizada a lo largo del manual en ejemplos, devuelve el tipo de su argumento. Dado que, como se mencionó anteriormente, los tipos son objetos, también tienen tipos, y podemos preguntar cuáles son sus tipos:

```jldoctest
julia> typeof(Rational{Int})
DataType

julia> typeof(Union{Real,String})
Union
```

¿Qué pasa si repetimos el proceso? ¿Cuál es el tipo de un tipo de un tipo? Como sucede, los tipos son todos valores compuestos y, por lo tanto, todos tienen un tipo de `DataType`:

```jldoctest
julia> typeof(DataType)
DataType

julia> typeof(Union)
DataType
```

`DataType` es su propio tipo.

Otra operación que se aplica a algunos tipos es [`supertype`](@ref), que revela el supertipo de un tipo. Solo los tipos declarados (`DataType`) tienen supertipos no ambiguos:

```jldoctest
julia> supertype(Float64)
AbstractFloat

julia> supertype(Number)
Any

julia> supertype(AbstractString)
Any

julia> supertype(Any)
Any
```

Si aplicas [`supertype`](@ref) a otros objetos de tipo (o a objetos no tipo), se genera un [`MethodError`](@ref):

```jldoctest; filter = r"Closest candidates.*"s
julia> supertype(Union{Float64,Int64})
ERROR: MethodError: no method matching supertype(::Type{Union{Float64, Int64}})
The function `supertype` exists, but no method is defined for this combination of argument types.

Closest candidates are:
[...]
```

## [Custom pretty-printing](@id man-custom-pretty-printing)

A menudo, uno quiere personalizar cómo se muestran las instancias de un tipo. Esto se logra sobrecargando la función [`show`](@ref). Por ejemplo, supongamos que definimos un tipo para representar números complejos en forma polar:

```jldoctest polartype
julia> struct Polar{T<:Real} <: Number
           r::T
           Θ::T
       end

julia> Polar(r::Real,Θ::Real) = Polar(promote(r,Θ)...)
Polar
```

Aquí, hemos añadido una función constructora personalizada para que pueda tomar argumentos de diferentes tipos [`Real`](@ref) y promoverlos a un tipo común (ver [Constructors](@ref man-constructors) y [Conversion and Promotion](@ref conversion-and-promotion)). (Por supuesto, tendríamos que definir muchos otros métodos también, para que actúe como un [`Number`](@ref), p. ej. `+`, `*`, `one`, `zero`, reglas de promoción y así sucesivamente). Por defecto, las instancias de este tipo se muestran de manera bastante simple, con información sobre el nombre del tipo y los valores de los campos, como por ejemplo `Polar{Float64}(3.0,4.0)`.

Si queremos que se muestre en su lugar como `3.0 * exp(4.0im)`, definiríamos el siguiente método para imprimir el objeto en un objeto de salida dado `io` (que representa un archivo, terminal, búfer, etcétera; ver [Networking and Streams](@ref)):

```jldoctest polartype
julia> Base.show(io::IO, z::Polar) = print(io, z.r, " * exp(", z.Θ, "im)")
```

Un control más detallado sobre la visualización de objetos `Polar` es posible. En particular, a veces se desea tanto un formato de impresión detallado en múltiples líneas, utilizado para mostrar un solo objeto en el REPL y otros entornos interactivos, como también un formato más compacto en una sola línea utilizado para [`print`](@ref) o para mostrar el objeto como parte de otro objeto (por ejemplo, en un array). Aunque por defecto se llama a la función `show(io, z)` en ambos casos, puedes definir un formato de múltiples líneas *diferente* para mostrar un objeto sobrecargando una forma de tres argumentos de `show` que toma el tipo MIME `text/plain` como su segundo argumento (ver [Multimedia I/O](@ref Multimedia-I/O)), por ejemplo:

```jldoctest polartype
julia> Base.show(io::IO, ::MIME"text/plain", z::Polar{T}) where{T} =
           print(io, "Polar{$T} complex number:\n   ", z)
```

(Tenga en cuenta que `print(..., z)` aquí llamará al método `show(io, z)` de 2 argumentos.) Esto resulta en:

```jldoctest polartype
julia> Polar(3, 4.0)
Polar{Float64} complex number:
   3.0 * exp(4.0im)

julia> [Polar(3, 4.0), Polar(4.0,5.3)]
2-element Vector{Polar{Float64}}:
 3.0 * exp(4.0im)
 4.0 * exp(5.3im)
```

donde se sigue utilizando la forma de una sola línea `show(io, z)` para un array de valores `Polar`. Técnicamente, el REPL llama a `display(z)` para mostrar el resultado de ejecutar una línea, que por defecto es `show(stdout, MIME("text/plain"), z)`, que a su vez por defecto es `show(stdout, z)`, pero no deberías *definir* nuevos métodos [`display`](@ref) a menos que estés definiendo un nuevo manejador de visualización multimedia (ver [Multimedia I/O](@ref Multimedia-I/O)).

Además, también puedes definir métodos `show` para otros tipos MIME con el fin de habilitar una visualización más rica (HTML, imágenes, etcétera) de objetos en entornos que lo soporten (por ejemplo, IJulia). Por ejemplo, podemos definir una visualización HTML formateada de objetos `Polar`, con superíndices y cursivas, a través de:

```jldoctest polartype
julia> Base.show(io::IO, ::MIME"text/html", z::Polar{T}) where {T} =
           println(io, "<code>Polar{$T}</code> complex number: ",
                   z.r, " <i>e</i><sup>", z.Θ, " <i>i</i></sup>")
```

Un objeto `Polar` se mostrará automáticamente utilizando HTML en un entorno que soporte la visualización de HTML, pero puedes llamar a `show` manualmente para obtener la salida en HTML si lo deseas:

```jldoctest polartype
julia> show(stdout, "text/html", Polar(3.0,4.0))
<code>Polar{Float64}</code> complex number: 3.0 <i>e</i><sup>4.0 <i>i</i></sup>
```

```@raw html
<p>An HTML renderer would display this as: <code>Polar{Float64}</code> complex number: 3.0 <i>e</i><sup>4.0 <i>i</i></sup></p>
```

Como regla general, el método `show` de una sola línea debería imprimir una expresión válida de Julia para crear el objeto mostrado. Cuando este método `show` contiene operadores infijos, como el operador de multiplicación (`*`) en nuestro método `show` de una sola línea para `Polar` arriba, puede que no se analice correctamente cuando se imprima como parte de otro objeto. Para ver esto, considera el objeto de expresión (ver [Program representation](@ref)) que toma el cuadrado de una instancia específica de nuestro tipo `Polar`:

```jldoctest polartype
julia> a = Polar(3, 4.0)
Polar{Float64} complex number:
   3.0 * exp(4.0im)

julia> print(:($a^2))
3.0 * exp(4.0im) ^ 2
```

Debido a que el operador `^` tiene una precedencia más alta que `*` (ver [Operator Precedence and Associativity](@ref)), esta salida no representa fielmente la expresión `a ^ 2`, que debería ser igual a `(3.0 * exp(4.0im)) ^ 2`. Para resolver este problema, debemos crear un método personalizado para `Base.show_unquoted(io::IO, z::Polar, indent::Int, precedence::Int)`, que se llama internamente por el objeto de expresión al imprimir:

```jldoctest polartype
julia> function Base.show_unquoted(io::IO, z::Polar, ::Int, precedence::Int)
           if Base.operator_precedence(:*) <= precedence
               print(io, "(")
               show(io, z)
               print(io, ")")
           else
               show(io, z)
           end
       end

julia> :($a^2)
:((3.0 * exp(4.0im)) ^ 2)
```

El método definido arriba agrega paréntesis alrededor de la llamada a `show` cuando la precedencia del operador de llamada es mayor o igual a la precedencia de la multiplicación. Esta verificación permite que las expresiones que se analizan correctamente sin los paréntesis (como `:($a + 2)` y `:($a == 2)`) los omitan al imprimir:

```jldoctest polartype
julia> :($a + 2)
:(3.0 * exp(4.0im) + 2)

julia> :($a == 2)
:(3.0 * exp(4.0im) == 2)
```

En algunos casos, es útil ajustar el comportamiento de los métodos `show` dependiendo del contexto. Esto se puede lograr a través del tipo [`IOContext`](@ref), que permite pasar propiedades contextuales junto con un flujo de IO envuelto. Por ejemplo, podemos construir una representación más corta en nuestro método `show` cuando la propiedad `:compact` está establecida en `true`, volviendo a la representación larga si la propiedad es `false` o está ausente:

```jldoctest polartype
julia> function Base.show(io::IO, z::Polar)
           if get(io, :compact, false)::Bool
               print(io, z.r, "ℯ", z.Θ, "im")
           else
               print(io, z.r, " * exp(", z.Θ, "im)")
           end
       end
```

Esta nueva representación compacta se utilizará cuando el flujo de IO pasado sea un objeto `IOContext` con la propiedad `:compact` establecida. En particular, este es el caso al imprimir arreglos con múltiples columnas (donde el espacio horizontal es limitado):

```jldoctest polartype
julia> show(IOContext(stdout, :compact=>true), Polar(3, 4.0))
3.0ℯ4.0im

julia> [Polar(3, 4.0) Polar(4.0,5.3)]
1×2 Matrix{Polar{Float64}}:
 3.0ℯ4.0im  4.0ℯ5.3im
```

Consulta la documentación de [`IOContext`](@ref) para obtener una lista de propiedades comunes que se pueden utilizar para ajustar la impresión.

## "Value types"

En Julia, no puedes despachar sobre un *valor* como `true` o `false`. Sin embargo, puedes despachar sobre tipos paramétricos, y Julia te permite incluir valores de "bits simples" (Tipos, Símbolos, Enteros, números de punto flotante, tuplas, etc.) como parámetros de tipo. Un ejemplo común es el parámetro de dimensionalidad en `Array{T,N}`, donde `T` es un tipo (por ejemplo, [`Float64`](@ref)), pero `N` es solo un `Int`.

Puedes crear tus propios tipos personalizados que tomen valores como parámetros y usarlos para controlar el despacho de tipos personalizados. A modo de ilustración de esta idea, introduzcamos el tipo paramétrico `Val{x}`, y su constructor `Val(x) = Val{x}()`, que sirve como una forma habitual de aprovechar esta técnica en casos donde no necesitas una jerarquía más elaborada.

[`Val`](@ref) se define como:

```jldoctest valtype
julia> struct Val{x}
       end

julia> Val(x) = Val{x}()
Val
```

No hay más en la implementación de `Val` que esto. Algunas funciones en la biblioteca estándar de Julia aceptan instancias de `Val` como argumentos, y también puedes usarlo para escribir tus propias funciones. Por ejemplo:

```jldoctest valtype
julia> firstlast(::Val{true}) = "First"
firstlast (generic function with 1 method)

julia> firstlast(::Val{false}) = "Last"
firstlast (generic function with 2 methods)

julia> firstlast(Val(true))
"First"

julia> firstlast(Val(false))
"Last"
```

Para la consistencia en Julia, el sitio de llamada siempre debe pasar una *instancia* de `Val` en lugar de usar un *tipo*, es decir, usa `foo(Val(:bar))` en lugar de `foo(Val{:bar})`.

Es importante señalar que es extremadamente fácil mal utilizar los tipos "valor" paramétricos, incluyendo `Val`; en casos desfavorables, puedes terminar haciendo que el rendimiento de tu código sea mucho *peor*. En particular, nunca querrías escribir código real como se ilustra arriba. Para obtener más información sobre los usos adecuados (e inadecuados) de `Val`, por favor lee [the more extensive discussion in the performance tips](@ref man-performance-value-type).

[^1]: "Small" is defined by the `max_union_splitting` configuration, which currently defaults to 4.

[^2]: A few popular languages have singleton types, including Haskell, Scala and Ruby.
