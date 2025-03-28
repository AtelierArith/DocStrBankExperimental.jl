# Style Guide

Las siguientes secciones explican algunos aspectos del estilo de codificación idiomático de Julia. Ninguna de estas reglas es absoluta; son solo sugerencias para ayudarte a familiarizarte con el lenguaje y para ayudarte a elegir entre diseños alternativos.

## Indentation

Usa 4 espacios por nivel de sangría.

## Write functions, not just scripts

Escribir código como una serie de pasos a nivel superior es una forma rápida de comenzar a resolver un problema, pero deberías intentar dividir un programa en funciones lo antes posible. Las funciones son más reutilizables y probables, y aclaran qué pasos se están realizando y cuáles son sus entradas y salidas. Además, el código dentro de las funciones tiende a ejecutarse mucho más rápido que el código a nivel superior, debido a cómo funciona el compilador de Julia.

También vale la pena enfatizar que las funciones deben tomar argumentos, en lugar de operar directamente sobre variables globales (aparte de constantes como [`pi`](@ref)).

## Avoid writing overly-specific types

El código debe ser lo más genérico posible. En lugar de escribir:

```julia
Complex{Float64}(x)
```

es mejor usar funciones genéricas disponibles:

```julia
complex(float(x))
```

La segunda versión convertirá `x` a un tipo apropiado, en lugar de siempre al mismo tipo.

Este punto de estilo es especialmente relevante para los argumentos de función. Por ejemplo, no declares un argumento como tipo `Int` o [`Int32`](@ref) si realmente podría ser cualquier entero, expresado con el tipo abstracto [`Integer`](@ref). De hecho, en muchos casos puedes omitir el tipo de argumento por completo, a menos que sea necesario para desambiguar de otras definiciones de métodos, ya que se lanzará un [`MethodError`](@ref) de todos modos si se pasa un tipo que no admite ninguna de las operaciones requeridas. (Esto se conoce como [duck typing](https://en.wikipedia.org/wiki/Duck_typing).)

Por ejemplo, considera las siguientes definiciones de una función `addone` que devuelve uno más su argumento:

```julia
addone(x::Int) = x + 1                 # works only for Int
addone(x::Integer) = x + oneunit(x)    # any integer type
addone(x::Number) = x + oneunit(x)     # any numeric type
addone(x) = x + oneunit(x)             # any type supporting + and oneunit
```

La última definición de `addone` maneja cualquier tipo que soporte [`oneunit`](@ref) (que devuelve 1 en el mismo tipo que `x`, lo que evita la promoción de tipo no deseada) y la función [`+`](@ref) con esos argumentos. La clave a darse cuenta es que *no hay penalización de rendimiento* por definir *solo* el general `addone(x) = x + oneunit(x)`, porque Julia compilará automáticamente versiones especializadas según sea necesario. Por ejemplo, la primera vez que llames a `addone(12)`, Julia compilará automáticamente una función `addone` especializada para argumentos `x::Int`, con la llamada a `oneunit` reemplazada por su valor en línea `1`. Por lo tanto, las primeras tres definiciones de `addone` anteriores son completamente redundantes con la cuarta definición.

## Handle excess argument diversity in the caller

En lugar de:

```julia
function foo(x, y)
    x = Int(x); y = Int(y)
    ...
end
foo(x, y)
```

usar:

```julia
function foo(x::Int, y::Int)
    ...
end
foo(Int(x), Int(y))
```

Este es un mejor estilo porque `foo` realmente no acepta números de todos los tipos; realmente necesita `Int`s.

Un problema aquí es que si una función requiere inherentemente enteros, podría ser mejor obligar al llamador a decidir cómo se deben convertir los no enteros (por ejemplo, redondeo hacia abajo o hacia arriba). Otro problema es que declarar tipos más específicos deja más "espacio" para futuras definiciones de métodos.

## [Append `!` to names of functions that modify their arguments](@id bang-convention)

En lugar de:

```julia
function double(a::AbstractArray{<:Number})
    for i in eachindex(a)
        a[i] *= 2
    end
    return a
end
```

usar:

```julia
function double!(a::AbstractArray{<:Number})
    for i in eachindex(a)
        a[i] *= 2
    end
    return a
end
```

Julia Base utiliza esta convención a lo largo y contiene ejemplos de funciones con formas tanto de copia como de modificación (por ejemplo, [`sort`](@ref) y [`sort!`](@ref)), y otras que son solo de modificación (por ejemplo, [`push!`](@ref), [`pop!`](@ref), [`splice!`](@ref)). Es típico que tales funciones también devuelvan el array modificado por conveniencia.

Las funciones relacionadas con IO o que utilizan generadores de números aleatorios (RNG) son excepciones notables: Dado que estas funciones casi invariablemente deben mutar el IO o el RNG, se utilizan funciones que terminan con `!` para significar una mutación *distinta* a la mutación del IO o el avance del estado del RNG. Por ejemplo, `rand(x)` muta el RNG, mientras que `rand!(x)` muta tanto el RNG como `x`; de manera similar, `read(io)` muta `io`, mientras que `read!(io, x)` muta ambos argumentos.

## Avoid strange type `Union`s

Tipos como `Union{Function,AbstractString}` a menudo son una señal de que algún diseño podría ser más limpio.

## Avoid elaborate container types

Por lo general, no es de mucha ayuda construir arreglos como el siguiente:

```julia
a = Vector{Union{Int,AbstractString,Tuple,Array}}(undef, n)
```

En este caso `Vector{Any}(undef, n)` es mejor. También es más útil para el compilador anotar usos específicos (por ejemplo, `a[i]::Int`) que intentar empaquetar muchas alternativas en un solo tipo.

## Prefer exported methods over direct field access

El código idiomático de Julia debería tratar generalmente los métodos exportados de un módulo como la interfaz a sus tipos. Los campos de un objeto se consideran generalmente detalles de implementación y el código del usuario solo debería acceder a ellos directamente si se indica que esto es parte de la API. Esto tiene varios beneficios:

  * Los desarrolladores de paquetes tienen más libertad para cambiar la implementación sin romper el código del usuario.
  * Los métodos se pueden pasar a construcciones de orden superior como [`map`](@ref) (por ejemplo, `map(imag, zs)`) en lugar de `[z.im for z in zs]`).
  * Los métodos se pueden definir en tipos abstractos.
  * Los métodos pueden describir una operación conceptual que se puede compartir entre tipos dispares (por ejemplo, `real(z)` funciona con números complejos o cuaterniones).

El sistema de despacho de Julia fomenta este estilo porque `play(x::MyType)` solo define el método `play` para ese tipo particular, dejando que otros tipos tengan su propia implementación.

De manera similar, las funciones no exportadas son típicamente internas y están sujetas a cambios, a menos que la documentación indique lo contrario. A veces, se les da un prefijo (o sufijo) `_` para sugerir aún más que algo es "interno" o un detalle de implementación, pero no es una regla.

Los contraejemplos a esta regla incluyen [`NamedTuple`](@ref), [`RegexMatch`](@ref match), [`StatStruct`](@ref stat).

## Use naming conventions consistent with Julia `base/`

  * los módulos y los nombres de tipo utilizan mayúsculas y camel case: `module SparseArrays`, `struct UnitRange`.
  * las funciones son minúsculas ([`maximum`](@ref), [`convert`](@ref)) y, cuando son legibles, con múltiples palabras unidas ([`isequal`](@ref), [`haskey`](@ref)). Cuando sea necesario, usa guiones bajos como separadores de palabras. Los guiones bajos también se utilizan para indicar una combinación de conceptos ([`remotecall_fetch`](@ref) como una implementación más eficiente de `fetch(remotecall(...))`) o como modificadores.
  * las funciones que mutan al menos uno de sus argumentos terminan en `!`.
  * La concisión es valorada, pero evita la abreviatura ([`indexin`](@ref) en lugar de `indxin`) ya que se vuelve difícil recordar si y cómo se abrevian ciertas palabras.

Si un nombre de función requiere múltiples palabras, considera si podría representar más de un concepto y si sería mejor dividirlo en partes.

## Write functions with argument ordering similar to Julia Base

Como regla general, la biblioteca Base utiliza el siguiente orden de argumentos para las funciones, según corresponda:

1. **Argumento de función**. Colocar un argumento de función primero permite el uso de [`do`](@ref) bloques para pasar funciones anónimas multilínea.
2. **Flujo de I/O**. Especificar el objeto `IO` primero permite pasar la función a funciones como [`sprint`](@ref), por ejemplo, `sprint(show, x)`.
3. **Entrada siendo mutada**. Por ejemplo, en [`fill!(x, v)`](@ref fill!), `x` es el objeto que se está mutando y aparece antes del valor que se va a insertar en `x`.
4. **Tipo**. Pasar un tipo típicamente significa que la salida tendrá el tipo dado. En [`parse(Int, "1")`](@ref parse), el tipo aparece antes de la cadena a analizar. Hay muchos ejemplos en los que el tipo aparece primero, pero es útil notar que en [`read(io, String)`](@ref read), el argumento `IO` aparece antes del tipo, lo cual está en consonancia con el orden descrito aquí.
5. **La entrada no está siendo mutada**. En `fill!(x, v)`, `v` *no* está siendo mutado y viene después de `x`.
6. **Clave**. Para colecciones asociativas, esta es la clave del par de clave-valor. Para otras colecciones indexadas, este es el índice.
7. **Valor**. Para colecciones asociativas, este es el valor del par clave-valor. En casos como [`fill!(x, v)`](@ref fill!), este es `v`.
8. **Todo lo demás**. Cualquier otro argumento.
9. **Varargs**. Esto se refiere a argumentos que se pueden listar indefinidamente al final de una llamada a función. Por ejemplo, en `Matrix{T}(undef, dims)`, las dimensiones se pueden dar como un [`Tuple`](@ref), p. ej. `Matrix{T}(undef, (1,2))`, o como [`Vararg`](@ref), p. ej. `Matrix{T}(undef, 1, 2)`.
10. **Argumentos de palabra clave**. En Julia, los argumentos de palabra clave deben ir al final en las definiciones de funciones; se enumeran aquí por el bien de la completitud.

La gran mayoría de las funciones no aceptarán todos los tipos de argumentos mencionados anteriormente; los números simplemente indican la precedencia que se debe utilizar para cualquier argumento aplicable a una función.

Por supuesto, hay algunas excepciones. Por ejemplo, en [`convert`](@ref), el tipo siempre debe ir primero. En [`setindex!`](@ref), el valor viene antes de los índices para que los índices puedan ser proporcionados como varargs.

Al diseñar APIs, adherirse a este orden general tanto como sea posible probablemente brindará a los usuarios de sus funciones una experiencia más consistente.

## Don't overuse try-catch

Es mejor evitar errores que depender de atraparlos.

## Don't parenthesize conditions

Julia no requiere paréntesis alrededor de las condiciones en `if` y `while`. Escribe:

```julia
if a == b
```

en lugar de:

```julia
if (a == b)
```

## Don't overuse `...`

La función de combinación de argumentos puede ser adictiva. En lugar de `[a..., b...]`, usa simplemente `[a; b]`, que ya concatena arreglos. [`collect(a)`](@ref) es mejor que `[a...]`, pero dado que `a` ya es iterable, a menudo es incluso mejor dejarlo como está y no convertirlo en un arreglo.

## Ensure constructors return an instance of their own type

Cuando se llama a un método `T(x)` en un tipo `T`, generalmente se espera que devuelva un valor del tipo T. Definir un [constructor](@ref man-constructors) que devuelva un tipo inesperado puede llevar a un comportamiento confuso e impredecible:

```jldoctest
julia> struct Foo{T}
           x::T
       end

julia> Base.Float64(foo::Foo) = Foo(Float64(foo.x))  # Do not define methods like this

julia> Float64(Foo(3))  # Should return `Float64`
Foo{Float64}(3.0)

julia> Foo{Int}(x) = Foo{Float64}(x)  # Do not define methods like this

julia> Foo{Int}(3)  # Should return `Foo{Int}`
Foo{Float64}(3.0)
```

Para mantener la claridad del código y asegurar la consistencia de tipos, siempre diseña los constructores para que devuelvan una instancia del tipo que se supone que deben construir.

## Don't use unnecessary static parameters

Una firma de función:

```julia
foo(x::T) where {T<:Real} = ...
```

debería escribirse como:

```julia
foo(x::Real) = ...
```

en su lugar, especialmente si `T` no se utiliza en el cuerpo de la función. Incluso si se utiliza `T`, se puede reemplazar con [`typeof(x)`](@ref) si es conveniente. No hay diferencia de rendimiento. Tenga en cuenta que esta no es una advertencia general contra los parámetros estáticos, solo contra los usos donde no son necesarios.

Tenga en cuenta también que los tipos de contenedores, específicamente, pueden necesitar parámetros de tipo en las llamadas a funciones. Consulte la FAQ [Avoid fields with abstract containers](@ref) para obtener más información.

## Avoid confusion about whether something is an instance or a type

Conjuntos de definiciones como el siguiente son confusos:

```julia
foo(::Type{MyType}) = ...
foo(::MyType) = foo(MyType)
```

Decida si el concepto en cuestión se escribirá como `MyType` o `MyType()`, y manténgase en ello.

El estilo preferido es usar instancias por defecto, y solo agregar métodos que involucren `Type{MyType}` más tarde si se vuelven necesarios para resolver algunos problemas.

Si un tipo es efectivamente una enumeración, debe definirse como un único tipo (idealmente inmutable, ya sea una estructura o un tipo primitivo), siendo los valores de la enumeración instancias de este. Los constructores y conversiones pueden verificar si los valores son válidos. Este diseño es preferido sobre hacer de la enumeración un tipo abstracto, con los "valores" como subtipos.

## Don't overuse macros

Ten en cuenta cuándo un macro podría ser realmente una función en su lugar.

Llamar a [`eval`](@ref) dentro de un macro es una señal de advertencia particularmente peligrosa; significa que el macro solo funcionará cuando se llame en el nivel superior. Si tal macro se escribe como una función en su lugar, naturalmente tendrá acceso a los valores de tiempo de ejecución que necesita.

## Don't expose unsafe operations at the interface level

Si tienes un tipo que utiliza un puntero nativo:

```julia
mutable struct NativeType
    p::Ptr{UInt8}
    ...
end
```

no escribas definiciones como la siguiente:

```julia
getindex(x::NativeType, i) = unsafe_load(x.p, i)
```

El problema es que los usuarios de este tipo pueden escribir `x[i]` sin darse cuenta de que la operación no es segura, y luego ser susceptibles a errores de memoria.

Tal función debería verificar la operación para asegurarse de que sea segura, o tener `unsafe` en alguna parte de su nombre para alertar a los llamadores.

## Don't overload methods of base container types

Es posible escribir definiciones como las siguientes:

```julia
show(io::IO, v::Vector{MyType}) = ...
```

Esto proporcionaría una visualización personalizada de vectores con un tipo de elemento nuevo específico. Aunque es tentador, esto debería evitarse. El problema es que los usuarios esperarán que un tipo bien conocido como `Vector()` se comporte de una manera determinada, y personalizar demasiado su comportamiento puede dificultar su uso.

## [Avoid type piracy](@id avoid-type-piracy)

"La "piratería de tipos" se refiere a la práctica de extender o redefinir métodos en Base u otros paquetes sobre tipos que no has definido. En casos extremos, puedes hacer que Julia se bloquee (por ejemplo, si tu extensión o redefinición de método causa que se pase una entrada inválida a un `ccall`). La piratería de tipos puede complicar el razonamiento sobre el código y puede introducir incompatibilidades que son difíciles de predecir y diagnosticar."

Como ejemplo, supongamos que deseas definir la multiplicación en símbolos en un módulo:

```julia
module A
import Base.*
*(x::Symbol, y::Symbol) = Symbol(x,y)
end
```

El problema es que ahora cualquier otro módulo que use `Base.*` también verá esta definición. Dado que `Symbol` está definido en Base y es utilizado por otros módulos, esto puede cambiar el comportamiento de código no relacionado de manera inesperada. Hay varias alternativas aquí, incluyendo usar un nombre de función diferente, o envolver los `Symbol`s en otro tipo que tú definas.

A veces, los paquetes acoplados pueden participar en la piratería de tipos para separar características de definiciones, especialmente cuando los paquetes fueron diseñados por autores colaboradores y cuando las definiciones son reutilizables. Por ejemplo, un paquete podría proporcionar algunos tipos útiles para trabajar con colores; otro paquete podría definir métodos para esos tipos que permiten conversiones entre espacios de color. Otro ejemplo podría ser un paquete que actúa como un envoltorio delgado para algún código en C, que otro paquete podría luego piratear para implementar una API de nivel superior, amigable con Julia.

## Be careful with type equality

Generalmente, quieres usar [`isa`](@ref) y [`<:`](@ref) para probar tipos, no `==`. Comprobar tipos para igualdad exacta típicamente solo tiene sentido al comparar con un tipo concreto conocido (por ejemplo, `T == Float64`), o si *realmente, realmente* sabes lo que estás haciendo.

## Don't write a trivial anonymous function `x->f(x)` for a named function `f`

Dado que las funciones de orden superior a menudo se llaman con funciones anónimas, es fácil concluir que esto es deseable o incluso necesario. Pero cualquier función se puede pasar directamente, sin ser "envuelta" en una función anónima. En lugar de escribir `map(x->f(x), a)`, escribe [`map(f, a)`](@ref).

## Avoid using floats for numeric literals in generic code when possible

Si escribes código genérico que maneja números, y que se espera que funcione con muchos argumentos de diferentes tipos numéricos, intenta usar literales de un tipo numérico que afecten a los argumentos lo menos posible a través de la promoción.

Por ejemplo,

```jldoctest
julia> f(x) = 2.0 * x
f (generic function with 1 method)

julia> f(1//2)
1.0

julia> f(1/2)
1.0

julia> f(1)
2.0
```

mientras

```jldoctest
julia> g(x) = 2 * x
g (generic function with 1 method)

julia> g(1//2)
1//1

julia> g(1/2)
1.0

julia> g(1)
2
```

Como puedes ver, la segunda versión, donde usamos un literal `Int`, preservó el tipo del argumento de entrada, mientras que la primera no lo hizo. Esto se debe a que, por ejemplo, `promote_type(Int, Float64) == Float64`, y la promoción ocurre con la multiplicación. De manera similar, los literales [`Rational`](@ref) son menos disruptivos para el tipo que los literales [`Float64`](@ref), pero más disruptivos que los `Int`s:

```jldoctest
julia> h(x) = 2//1 * x
h (generic function with 1 method)

julia> h(1//2)
1//1

julia> h(1/2)
1.0

julia> h(1)
2//1
```

Así, utiliza literales `Int` cuando sea posible, con `Rational{Int}` para números literales no enteros, con el fin de facilitar el uso de tu código.
