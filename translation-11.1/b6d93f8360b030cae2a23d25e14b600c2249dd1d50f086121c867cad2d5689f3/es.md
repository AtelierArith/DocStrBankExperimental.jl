# [Functions](@id man-functions)

En Julia, una función es un objeto que mapea una tupla de valores de argumento a un valor de retorno. Las funciones de Julia no son funciones matemáticas puras, porque pueden alterar y ser afectadas por el estado global del programa. La sintaxis básica para definir funciones en Julia es:

```jldoctest
julia> function f(x, y)
           x + y
       end
f (generic function with 1 method)
```

Esta función acepta dos argumentos `x` e `y` y devuelve el valor de la última expresión evaluada, que es `x + y`.

Hay una segunda sintaxis más concisa para definir una función en Julia. La sintaxis tradicional de declaración de funciones demostrada arriba es equivalente a la siguiente "forma de asignación" compacta:

```jldoctest fofxy
julia> f(x, y) = x + y
f (generic function with 1 method)
```

En el formulario de asignación, el cuerpo de la función debe ser una única expresión, aunque puede ser una expresión compuesta (ver [Compound Expressions](@ref man-compound-expressions)). Las definiciones de funciones cortas y simples son comunes en Julia. La sintaxis de función corta es, por lo tanto, bastante idiomática, reduciendo considerablemente tanto la escritura como el ruido visual.

Una función se llama utilizando la sintaxis tradicional de paréntesis:

```jldoctest fofxy
julia> f(2, 3)
5
```

Sin paréntesis, la expresión `f` se refiere al objeto de la función y puede ser pasada como cualquier otro valor:

```jldoctest fofxy
julia> g = f;

julia> g(2, 3)
5
```

Al igual que con las variables, Unicode también se puede utilizar para nombres de funciones:

```jldoctest
julia> ∑(x, y) = x + y
∑ (generic function with 1 method)

julia> ∑(2, 3)
5
```

## [Argument Passing Behavior](@id man-argument-passing)

Los argumentos de las funciones de Julia siguen una convención a veces llamada "paso por referencia", lo que significa que los valores no se copian cuando se pasan a las funciones. Los argumentos de la función en sí actúan como nuevos *vínculos* de variables (nuevos "nombres" que pueden referirse a valores), muy parecido a [assignments](@ref man-assignment-expressions) `argument_name = argument_value`, de modo que los objetos a los que se refieren son idénticos a los valores pasados. Las modificaciones a los valores mutables (como los `Array`) realizadas dentro de una función serán visibles para el llamador. (Este es el mismo comportamiento que se encuentra en Scheme, la mayoría de los Lisps, Python, Ruby y Perl, entre otros lenguajes dinámicos.)

Por ejemplo, en la función

```julia
function f(x, y)
    x[1] = 42    # mutates x
    y = 7 + y    # new binding for y, no mutation
    return y
end
```

La declaración `x[1] = 42` *muta* el objeto `x`, y por lo tanto este cambio *será* visible en el arreglo pasado por el llamador para este argumento. Por otro lado, la asignación `y = 7 + y` cambia el *vínculo* ("nombre") `y` para referirse a un nuevo valor `7 + y`, en lugar de mutar el *objeto original* al que se refiere `y`, y por lo tanto *no* cambia el argumento correspondiente pasado por el llamador. Esto se puede ver si llamamos a `f(x, y)`:

```julia-repl
julia> a = [4, 5, 6]
3-element Vector{Int64}:
 4
 5
 6

julia> b = 3
3

julia> f(a, b) # returns 7 + b == 10
10

julia> a  # a[1] is changed to 42 by f
3-element Vector{Int64}:
 42
  5
  6

julia> b  # not changed
3
```

Como una convención común en Julia (no un requisito sintáctico), tal función sería [typically be named `f!(x, y)`](@ref man-punctuation) en lugar de `f(x, y)`, como un recordatorio visual en el sitio de llamada de que al menos uno de los argumentos (a menudo el primero) está siendo mutado.

!!! warning "Shared memory between arguments"
    El comportamiento de una función mutante puede ser inesperado cuando un argumento mutado comparte memoria con otro argumento, una situación conocida como aliasing (por ejemplo, cuando uno es una vista del otro). A menos que la documentación de la función indique explícitamente que el aliasing produce el resultado esperado, es responsabilidad del llamador garantizar un comportamiento adecuado con tales entradas.


## Argument-type declarations

Puedes declarar los tipos de los argumentos de la función añadiendo `::TypeName` al nombre del argumento, como es habitual para [Type Declarations](@ref) en Julia. Por ejemplo, la siguiente función calcula [Fibonacci numbers](https://en.wikipedia.org/wiki/Fibonacci_number) de forma recursiva:

```
fib(n::Integer) = n ≤ 2 ? one(n) : fib(n-1) + fib(n-2)
```

y la especificación `::Integer` significa que solo será invocable cuando `n` sea un subtipo del tipo [abstract](@ref man-abstract-types) `Integer`.

Las declaraciones de tipos de argumentos **normalmente no tienen impacto en el rendimiento**: independientemente de qué tipos de argumentos (si los hay) se declaren, Julia compila una versión especializada de la función para los tipos de argumentos reales pasados por el llamador. Por ejemplo, llamar a `fib(1)` activará la compilación de una versión especializada de `fib` optimizada específicamente para argumentos de tipo `Int`, que luego se reutiliza si se llaman `fib(7)` o `fib(15)`. (Hay raras excepciones cuando una declaración de tipo de argumento puede activar especializaciones adicionales del compilador; véase: [Be aware of when Julia avoids specializing](@ref).) Las razones más comunes para declarar tipos de argumentos en Julia son, en cambio:

  * **Despacho:** Como se explicó en [Methods](@ref), puedes tener diferentes versiones ("métodos") de una función para diferentes tipos de argumentos, en cuyo caso los tipos de argumentos se utilizan para determinar qué implementación se llama para qué argumentos. Por ejemplo, podrías implementar un algoritmo completamente diferente `fib(x::Number) = ...` que funcione para cualquier tipo `Number` utilizando [Binet's formula](https://en.wikipedia.org/wiki/Fibonacci_number#Binet%27s_formula) para extenderlo a valores no enteros.
  * **Corrección:** Las declaraciones de tipo pueden ser útiles si tu función solo devuelve resultados correctos para ciertos tipos de argumentos. Por ejemplo, si omitiéramos los tipos de argumento y escribiéramos `fib(n) = n ≤ 2 ? one(n) : fib(n-1) + fib(n-2)`, entonces `fib(1.5)` nos daría silenciosamente la respuesta sin sentido `1.0`.
  * **Claridad:** Las declaraciones de tipo pueden servir como una forma de documentación sobre los argumentos esperados.

Sin embargo, es un **error común restringir demasiado los tipos de argumentos**, lo que puede limitar innecesariamente la aplicabilidad de la función y evitar que se reutilice en circunstancias que no anticipaste. Por ejemplo, la función `fib(n::Integer)` anterior funciona igualmente bien para argumentos de `Int` (enteros de máquina) y `BigInt` (enteros de precisión arbitraria) (ver [BigFloats and BigInts](@ref BigFloats-and-BigInts)), lo cual es especialmente útil porque los números de Fibonacci crecen exponencialmente rápido y rápidamente desbordarán cualquier tipo de precisión fija como `Int` (ver [Overflow behavior](@ref)). Sin embargo, si hubiéramos declarado nuestra función como `fib(n::Int)`, la aplicación a `BigInt` habría sido impedida sin razón. En general, debes usar los tipos abstractos más generales aplicables para los argumentos, y **cuando tengas dudas, omite los tipos de argumentos**. Siempre puedes agregar especificaciones de tipo de argumento más tarde si se vuelven necesarias, y no sacrificas rendimiento ni funcionalidad al omitirlos.

## The `return` Keyword

El valor devuelto por una función es el valor de la última expresión evaluada, que, por defecto, es la última expresión en el cuerpo de la definición de la función. En la función de ejemplo, `f`, de la sección anterior, este es el valor de la expresión `x + y`. Como alternativa, al igual que en muchos otros lenguajes, la palabra clave `return` hace que una función devuelva inmediatamente, proporcionando una expresión cuyo valor se devuelve:

```julia
function g(x, y)
    return x * y
    x + y
end
```

Dado que las definiciones de funciones se pueden ingresar en sesiones interactivas, es fácil comparar estas definiciones:

```jldoctest
julia> f(x, y) = x + y
f (generic function with 1 method)

julia> function g(x, y)
           return x * y
           x + y
       end
g (generic function with 1 method)

julia> f(2, 3)
5

julia> g(2, 3)
6
```

Por supuesto, en un cuerpo de función puramente lineal como `g`, el uso de `return` es inútil ya que la expresión `x + y` nunca se evalúa y podríamos simplemente hacer de `x * y` la última expresión en la función y omitir el `return`. Sin embargo, en conjunto con otro flujo de control, `return` es realmente útil. Aquí, por ejemplo, hay una función que calcula la longitud de la hipotenusa de un triángulo rectángulo con lados de longitud `x` y `y`, evitando desbordamientos:

```jldoctest
julia> function hypot(x, y)
           x = abs(x)
           y = abs(y)
           if x > y
               r = y/x
               return x*sqrt(1 + r*r)
           end
           if y == 0
               return zero(x)
           end
           r = x/y
           return y*sqrt(1 + r*r)
       end
hypot (generic function with 1 method)

julia> hypot(3, 4)
5.0
```

Hay tres posibles puntos de retorno de esta función, devolviendo los valores de tres expresiones diferentes, dependiendo de los valores de `x` e `y`. El `return` en la última línea podría omitirse ya que es la última expresión.

### [Return type](@id man-functions-return-type)

Un tipo de retorno se puede especificar en la declaración de la función utilizando el operador `::`. Esto convierte el valor de retorno al tipo especificado.

```jldoctest
julia> function g(x, y)::Int8
           return x * y
       end;

julia> typeof(g(1, 2))
Int8
```

Esta función siempre devolverá un `Int8` independientemente de los tipos de `x` e `y`. Consulta [Type Declarations](@ref) para obtener más información sobre los tipos de retorno.

Las declaraciones de tipo de retorno son **raramente utilizadas** en Julia: en general, deberías escribir funciones "estables en tipo" en las que el compilador de Julia pueda inferir automáticamente el tipo de retorno. Para más información, consulta el capítulo [Performance Tips](@ref man-performance-tips).

### Returning nothing

Para funciones que no necesitan devolver un valor (funciones que se utilizan solo para algunos efectos secundarios), la convención de Julia es devolver el valor [`nothing`](@ref):

```julia
function printx(x)
    println("x = $x")
    return nothing
end
```

Esto es una *convención* en el sentido de que `nothing` no es una palabra clave de Julia, sino solo un objeto singleton de tipo `Nothing`. Además, puede notar que el ejemplo de la función `printx` anterior es artificial, porque `println` ya devuelve `nothing`, por lo que la línea `return` es redundante.

Hay dos formas posibles abreviadas para la expresión `return nothing`. Por un lado, la palabra clave `return` devuelve implícitamente `nothing`, por lo que se puede usar sola. Por otro lado, dado que las funciones devuelven implícitamente su última expresión evaluada, `nothing` se puede usar solo cuando es la última expresión. La preferencia por la expresión `return nothing` en lugar de `return` o `nothing` solo es una cuestión de estilo de codificación.

## Operators Are Functions

En Julia, la mayoría de los operadores son simplemente funciones con soporte para una sintaxis especial. (Las excepciones son los operadores con semánticas de evaluación especiales como `&&` y `||`. Estos operadores no pueden ser funciones ya que [Short-Circuit Evaluation](@ref) requiere que sus operandos no se evalúen antes de la evaluación del operador). En consecuencia, también puedes aplicarlos utilizando listas de argumentos entre paréntesis, tal como lo harías con cualquier otra función:

```jldoctest
julia> 1 + 2 + 3
6

julia> +(1, 2, 3)
6
```

La forma infija es exactamente equivalente a la forma de aplicación de función; de hecho, la primera se analiza para producir la llamada a la función internamente. Esto también significa que puedes asignar y pasar operadores como [`+`](@ref) y [`*`](@ref) tal como lo harías con otros valores de función:

```jldoctest
julia> f = +;

julia> f(1, 2, 3)
6
```

Bajo el nombre `f`, la función no admite notación infija, sin embargo.

## Operators With Special Names

Unas pocas expresiones especiales corresponden a llamadas a funciones con nombres no obvios. Estas son:

| Expression            | Calls                                    |
|:--------------------- |:---------------------------------------- |
| `[A B C ...]`         | [`hcat`](@ref)                           |
| `[A; B; C; ...]`      | [`vcat`](@ref)                           |
| `[A B; C D; ...]`     | [`hvcat`](@ref)                          |
| `[A; B;; C; D;; ...]` | [`hvncat`](@ref)                         |
| `A'`                  | [`adjoint`](@ref)                        |
| `A[i]`                | [`getindex`](@ref)                       |
| `A[i] = x`            | [`setindex!`](@ref)                      |
| `A.n`                 | [`getproperty`](@ref Base.getproperty)   |
| `A.n = x`             | [`setproperty!`](@ref Base.setproperty!) |

Tenga en cuenta que expresiones similares a `[A; B;; C; D;; ...]` pero con más de dos `;` consecutivos también corresponden a llamadas a `hvncat`.

## [Anonymous Functions](@id man-anonymous-functions)

Las funciones en Julia son [first-class objects](https://en.wikipedia.org/wiki/First-class_citizen): se pueden asignar a variables y se pueden llamar utilizando la sintaxis estándar de llamada a funciones desde la variable a la que se han asignado. Pueden ser utilizadas como argumentos y pueden ser devueltas como valores. También se pueden crear de forma anónima, sin ser nombradas, utilizando cualquiera de estas sintaxis:

```jldoctest
julia> x -> x^2 + 2x - 1
#1 (generic function with 1 method)

julia> function (x)
           x^2 + 2x - 1
       end
#3 (generic function with 1 method)
```

Cada declaración crea una función que toma un argumento `x` y devuelve el valor del polinomio `x^2 + 2x - 1` en ese valor. Observe que el resultado es una función genérica, pero con un nombre generado por el compilador basado en la numeración consecutiva.

El uso principal de las funciones anónimas es pasarlas a funciones que toman otras funciones como argumentos. Un ejemplo clásico es [`map`](@ref), que aplica una función a cada valor de un array y devuelve un nuevo array que contiene los valores resultantes:

```jldoctest
julia> map(round, [1.2, 3.5, 1.7])
3-element Vector{Float64}:
 1.0
 4.0
 2.0
```

Esto está bien si ya existe una función nombrada que efectúe la transformación para pasar como el primer argumento a [`map`](@ref). Sin embargo, a menudo no existe una función nombrada lista para usar. En estas situaciones, el constructo de función anónima permite la creación fácil de un objeto de función de un solo uso sin necesidad de un nombre:

```jldoctest
julia> map(x -> x^2 + 2x - 1, [1, 3, -1])
3-element Vector{Int64}:
  2
 14
 -2
```

Una función anónima que acepta múltiples argumentos se puede escribir utilizando la sintaxis `(x,y,z)->2x+y-z`.

Las declaraciones de tipo de argumento para funciones anónimas funcionan como para funciones nombradas, por ejemplo `x::Integer->2x`. No se puede especificar el tipo de retorno de una función anónima.

Una función anónima sin argumentos se puede escribir como `()->2+2`. La idea de una función sin argumentos puede parecer extraña, pero es útil en casos donde un resultado no puede (o no debe) ser precomputado. Por ejemplo, Julia tiene una función [`time`](@ref) sin argumentos que devuelve el tiempo actual en segundos, y así `seconds = ()->round(Int, time())` es una función anónima que devuelve este tiempo redondeado al entero más cercano asignado a la variable `seconds`. Cada vez que se llama a esta función anónima como `seconds()`, se calculará y devolverá el tiempo actual.

## Tuples

Julia tiene una estructura de datos incorporada llamada *tupla* que está estrechamente relacionada con los argumentos de función y los valores de retorno. Una tupla es un contenedor de longitud fija que puede contener cualquier valor, pero no se puede modificar (es *inmutable*). Las tuplas se construyen con comas y paréntesis, y se pueden acceder a través de la indexación:

```jldoctest
julia> (1, 1+1)
(1, 2)

julia> (1,)
(1,)

julia> x = (0.0, "hello", 6*7)
(0.0, "hello", 42)

julia> x[2]
"hello"
```

Tenga en cuenta que una tupla de longitud 1 debe escribirse con una coma, `(1,)`, ya que `(1)` sería solo un valor entre paréntesis. `()` representa la tupla vacía (de longitud 0).

## Named Tuples

Los componentes de las tuplas pueden tener nombres opcionales, en cuyo caso se construye una *tupla nombrada*:

```jldoctest
julia> x = (a=2, b=1+2)
(a = 2, b = 3)

julia> x[1]
2

julia> x.a
2
```

Los campos de las tuplas nombradas se pueden acceder por nombre utilizando la sintaxis de punto (`x.a`) además de la sintaxis de indexación regular (`x[1]` o `x[:a]`).

## [Destructuring Assignment and Multiple Return Values](@id destructuring-assignment)

Una lista de variables separadas por comas (opcionalmente envueltas en paréntesis) puede aparecer en el lado izquierdo de una asignación: el valor en el lado derecho es *desestructurado* iterando y asignando a cada variable a su vez:

```jldoctest
julia> (a, b, c) = 1:3
1:3

julia> b
2
```

El valor a la derecha debe ser un iterador (ver [Iteration interface](@ref man-interface-iteration)) al menos tan largo como el número de variables a la izquierda (cualquier elemento adicional del iterador se ignora).

Esto se puede usar para devolver múltiples valores de funciones al devolver una tupla u otro valor iterable. Por ejemplo, la siguiente función devuelve dos valores:

```jldoctest foofunc
julia> function foo(a, b)
           a+b, a*b
       end
foo (generic function with 1 method)
```

Si lo llamas en una sesión interactiva sin asignar el valor de retorno en ningún lugar, verás la tupla devuelta:

```jldoctest foofunc
julia> foo(2, 3)
(5, 6)
```

La asignación por desestructuración extrae cada valor en una variable:

```jldoctest foofunc
julia> x, y = foo(2, 3)
(5, 6)

julia> x
5

julia> y
6
```

Otro uso común es para intercambiar variables:

```jldoctest foofunc
julia> y, x = x, y
(5, 6)

julia> x
6

julia> y
5
```

Si solo se requiere un subconjunto de los elementos del iterador, una convención común es asignar los elementos ignorados a una variable que consista únicamente en guiones bajos `_` (que es un nombre de variable de otro modo inválido, ver [Allowed Variable Names](@ref man-allowed-variable-names)):

```jldoctest
julia> _, _, _, d = 1:10
1:10

julia> d
4
```

Otras expresiones válidas del lado izquierdo se pueden usar como elementos de la lista de asignación, que llamarán a [`setindex!`](@ref) o [`setproperty!`](@ref), o desestructurar recursivamente elementos individuales del iterador:

```jldoctest
julia> X = zeros(3);

julia> X[1], (a, b) = (1, (2, 3))
(1, (2, 3))

julia> X
3-element Vector{Float64}:
 1.0
 0.0
 0.0

julia> a
2

julia> b
3
```

!!! compat "Julia 1.6"
    `...` con la asignación requiere Julia 1.6


Si el último símbolo en la lista de asignación está seguido por `...` (conocido como *slurping*), entonces se le asignará una colección o un iterador perezoso de los elementos restantes del iterador del lado derecho:

```jldoctest
julia> a, b... = "hello"
"hello"

julia> a
'h': ASCII/Unicode U+0068 (category Ll: Letter, lowercase)

julia> b
"ello"

julia> a, b... = Iterators.map(abs2, 1:4)
Base.Generator{UnitRange{Int64}, typeof(abs2)}(abs2, 1:4)

julia> a
1

julia> b
Base.Iterators.Rest{Base.Generator{UnitRange{Int64}, typeof(abs2)}, Int64}(Base.Generator{UnitRange{Int64}, typeof(abs2)}(abs2, 1:4), 1)
```

Vea [`Base.rest`](@ref) para obtener detalles sobre el manejo preciso y la personalización de iteradores específicos.

!!! compat "Julia 1.9"
    `...` en posición no final de una asignación requiere Julia 1.9


El sorber en las tareas también puede ocurrir en cualquier otra posición. A diferencia de sorber el final de una colección, sin embargo, esto siempre será ansioso.

```jldoctest
julia> a, b..., c = 1:5
1:5

julia> a
1

julia> b
3-element Vector{Int64}:
 2
 3
 4

julia> c
5

julia> front..., tail = "Hi!"
"Hi!"

julia> front
"Hi"

julia> tail
'!': ASCII/Unicode U+0021 (category Po: Punctuation, other)
```

Esto se implementa en términos de la función [`Base.split_rest`](@ref).

Tenga en cuenta que para las definiciones de funciones variádicas, el slurping solo se permite en la posición final. Sin embargo, esto no se aplica a [single argument destructuring](@ref man-argument-destructuring), ya que eso no afecta la dispatch de métodos:

```jldoctest
julia> f(x..., y) = x
ERROR: syntax: invalid "..." on non-final argument
Stacktrace:
[...]

julia> f((x..., y)) = x
f (generic function with 1 method)

julia> f((1, 2, 3))
(1, 2)
```

## Property destructuring

En lugar de desestructurar basándose en la iteración, el lado derecho de las asignaciones también se puede desestructurar utilizando nombres de propiedades. Esto sigue la sintaxis para NamedTuples y funciona asignando a cada variable a la izquierda una propiedad del lado derecho de la asignación con el mismo nombre utilizando `getproperty`:

```jldoctest
julia> (; b, a) = (a=1, b=2, c=3)
(a = 1, b = 2, c = 3)

julia> a
1

julia> b
2
```

## [Argument destructuring](@id man-argument-destructuring)

La característica de desestructuración también se puede utilizar dentro de un argumento de función. Si el nombre de un argumento de función se escribe como una tupla (por ejemplo, `(x, y)`) en lugar de solo un símbolo, entonces se insertará una asignación `(x, y) = argumento` por ti:

```julia-repl
julia> minmax(x, y) = (y < x) ? (y, x) : (x, y)

julia> gap((min, max)) = max - min

julia> gap(minmax(10, 2))
8
```

Nota el conjunto extra de paréntesis en la definición de `gap`. Sin ellos, `gap` sería una función de dos argumentos, y este ejemplo no funcionaría.

De manera similar, la desestructuración de propiedades también se puede utilizar para los argumentos de función:

```julia-repl
julia> foo((; x, y)) = x + y
foo (generic function with 1 method)

julia> foo((x=1, y=2))
3

julia> struct A
           x
           y
       end

julia> foo(A(3, 4))
7
```

Para funciones anónimas, desestructurar un solo argumento requiere una coma extra:

```
julia> map(((x, y),) -> x + y, [(1, 2), (3, 4)])
2-element Array{Int64,1}:
 3
 7
```

## Varargs Functions

A menudo es conveniente poder escribir funciones que acepten un número arbitrario de argumentos. Tales funciones se conocen tradicionalmente como funciones "varargs", que es una abreviatura de "número variable de argumentos". Puedes definir una función varargs siguiendo el último argumento posicional con una elipsis:

```jldoctest barfunc
julia> bar(a, b, x...) = (a, b, x)
bar (generic function with 1 method)
```

Las variables `a` y `b` están vinculadas a los dos primeros valores de argumento como es habitual, y la variable `x` está vinculada a una colección iterable de cero o más valores pasados a `bar` después de sus dos primeros argumentos:

```jldoctest barfunc
julia> bar(1, 2)
(1, 2, ())

julia> bar(1, 2, 3)
(1, 2, (3,))

julia> bar(1, 2, 3, 4)
(1, 2, (3, 4))

julia> bar(1, 2, 3, 4, 5, 6)
(1, 2, (3, 4, 5, 6))
```

En todos estos casos, `x` está vinculado a una tupla de los valores finales pasados a `bar`.

Es posible restringir el número de valores pasados como un argumento variable; esto se discutirá más adelante en [Parametrically-constrained Varargs methods](@ref).

Por otro lado, a menudo es útil "desglosar" los valores contenidos en una colección iterable en una llamada a función como argumentos individuales. Para hacer esto, también se utiliza `...` pero en la llamada a la función en su lugar:

```jldoctest barfunc
julia> x = (3, 4)
(3, 4)

julia> bar(1, 2, x...)
(1, 2, (3, 4))
```

En este caso, una tupla de valores se inserta en una llamada de varargs precisamente donde van el número variable de argumentos. Sin embargo, esto no tiene que ser así:

```jldoctest barfunc
julia> x = (2, 3, 4)
(2, 3, 4)

julia> bar(1, x...)
(1, 2, (3, 4))

julia> x = (1, 2, 3, 4)
(1, 2, 3, 4)

julia> bar(x...)
(1, 2, (3, 4))
```

Además, el objeto iterable desglosado en una llamada a función no tiene que ser una tupla:

```jldoctest barfunc
julia> x = [3, 4]
2-element Vector{Int64}:
 3
 4

julia> bar(1, 2, x...)
(1, 2, (3, 4))

julia> x = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> bar(x...)
(1, 2, (3, 4))
```

Además, la función a la que se pasan los argumentos no necesita ser una función varargs (aunque a menudo lo es):

```jldoctest
julia> baz(a, b) = a + b;

julia> args = [1, 2]
2-element Vector{Int64}:
 1
 2

julia> baz(args...)
3

julia> args = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> baz(args...)
ERROR: MethodError: no method matching baz(::Int64, ::Int64, ::Int64)
The function `baz` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  baz(::Any, ::Any)
   @ Main none:1

Stacktrace:
[...]
```

Como puedes ver, si el número incorrecto de elementos está en el contenedor expandido, entonces la llamada a la función fallará, tal como lo haría si se dieran demasiados argumentos de manera explícita.

## Optional Arguments

A menudo es posible proporcionar valores predeterminados sensatos para los argumentos de las funciones. Esto puede ahorrar a los usuarios tener que pasar cada argumento en cada llamada. Por ejemplo, la función [`Date(y, [m, d])`](@ref) del módulo `Dates` construye un tipo `Date` para un año dado `y`, mes `m` y día `d`. Sin embargo, los argumentos `m` y `d` son opcionales y su valor predeterminado es `1`. Este comportamiento se puede expresar de manera concisa como:

```jldoctest date_default_args
julia> using Dates

julia> function date(y::Int64, m::Int64=1, d::Int64=1)
           err = Dates.validargs(Date, y, m, d)
           err === nothing || throw(err)
           return Date(Dates.UTD(Dates.totaldays(y, m, d)))
       end
date (generic function with 3 methods)
```

Observe, que esta definición llama a otro método de la función `Date` que toma un argumento de tipo `UTInstant{Day}`.

Con esta definición, la función se puede llamar con uno, dos o tres argumentos, y `1` se pasa automáticamente cuando solo se especifican uno o dos de los argumentos:

```jldoctest date_default_args
julia> date(2000, 12, 12)
2000-12-12

julia> date(2000, 12)
2000-12-01

julia> date(2000)
2000-01-01
```

Los argumentos opcionales son en realidad solo una sintaxis conveniente para escribir múltiples definiciones de métodos con diferentes números de argumentos (ver [Note on Optional and keyword Arguments](@ref)). Esto se puede verificar para nuestro ejemplo de la función `date` llamando a la función `methods`:

```julia-repl
julia> methods(date)
# 3 methods for generic function "date":
[1] date(y::Int64) in Main at REPL[1]:1
[2] date(y::Int64, m::Int64) in Main at REPL[1]:1
[3] date(y::Int64, m::Int64, d::Int64) in Main at REPL[1]:1
```

## Keyword Arguments

Algunas funciones necesitan un gran número de argumentos, o tienen un gran número de comportamientos. Recordar cómo llamar a tales funciones puede ser difícil. Los argumentos de palabra clave pueden hacer que estas interfaces complejas sean más fáciles de usar y extender al permitir que los argumentos se identifiquen por nombre en lugar de solo por posición.

Por ejemplo, considera una función `plot` que traza una línea. Esta función podría tener muchas opciones para controlar el estilo de la línea, el ancho, el color, y así sucesivamente. Si acepta argumentos de palabra clave, una llamada posible podría verse como `plot(x, y, width=2)`, donde hemos elegido especificar solo el ancho de la línea. Observa que esto cumple dos propósitos. La llamada es más fácil de leer, ya que podemos etiquetar un argumento con su significado. También se vuelve posible pasar cualquier subconjunto de un gran número de argumentos, en cualquier orden.

Las funciones con argumentos de palabra clave se definen utilizando un punto y coma en la firma:

```julia
function plot(x, y; style="solid", width=1, color="black")
    ###
end
```

Cuando se llama a la función, el punto y coma es opcional: se puede llamar a `plot(x, y, width=2)` o `plot(x, y; width=2)`, pero el primer estilo es más común. Un punto y coma explícito es necesario solo para pasar varargs o palabras clave computadas como se describe a continuación.

Los valores predeterminados de los argumentos de palabra clave se evalúan solo cuando es necesario (cuando no se pasa un argumento de palabra clave correspondiente) y en orden de izquierda a derecha. Por lo tanto, las expresiones predeterminadas pueden hacer referencia a argumentos de palabra clave anteriores.

Los tipos de argumentos de palabra clave se pueden hacer explícitos de la siguiente manera:

```julia
function f(; x::Int=1)
    ###
end
```

Los argumentos de palabra clave también se pueden usar en funciones varargs:

```julia
function plot(x...; style="solid")
    ###
end
```

Los argumentos clave adicionales se pueden recopilar utilizando `...`, como en las funciones varargs:

```julia
function f(x; y=0, kwargs...)
    ###
end
```

Dentro de `f`, `kwargs` será un iterador de clave-valor inmutable sobre una tupla nombrada. Las tuplas nombradas (así como los diccionarios con claves de `Symbol`, y otros iteradores que producen colecciones de dos valores con símbolo como primer valor) se pueden pasar como argumentos de palabra clave utilizando un punto y coma en una llamada, por ejemplo, `f(x, z=1; kwargs...)`.

Si un argumento de palabra clave no tiene un valor predeterminado asignado en la definición del método, entonces es *requerido*: se lanzará una excepción [`UndefKeywordError`](@ref) si el llamador no le asigna un valor:

```julia
function f(x; y)
    ###
end
f(3, y=5) # ok, y is assigned
f(3)      # throws UndefKeywordError(:y)
```

También se pueden pasar expresiones `clave => valor` después de un punto y coma. Por ejemplo, `plot(x, y; :width => 2)` es equivalente a `plot(x, y, width=2)`. Esto es útil en situaciones donde el nombre de la palabra clave se calcula en tiempo de ejecución.

Cuando un identificador desnudo o una expresión de punto ocurre después de un punto y coma, el nombre del argumento clave se implica por el identificador o el nombre del campo. Por ejemplo, `plot(x, y; width)` es equivalente a `plot(x, y; width=width)` y `plot(x, y; options.width)` es equivalente a `plot(x, y; width=options.width)`.

La naturaleza de los argumentos de palabra clave hace posible especificar el mismo argumento más de una vez. Por ejemplo, en la llamada `plot(x, y; options..., width=2)` es posible que la estructura `options` también contenga un valor para `width`. En tal caso, la ocurrencia más a la derecha tiene prioridad; en este ejemplo, `width` tiene la certeza de tener el valor `2`. Sin embargo, especificar explícitamente el mismo argumento de palabra clave múltiples veces, por ejemplo `plot(x, y, width=2, width=3)`, no está permitido y resulta en un error de sintaxis.

## Evaluation Scope of Default Values

Cuando se evalúan las expresiones por defecto de los argumentos opcionales y de palabra clave, solo los *argumentos anteriores* están en el ámbito. Por ejemplo, dada esta definición:

```julia
function f(x, a=b, b=1)
    ###
end
```

el `b` en `a=b` se refiere a un `b` en un ámbito externo, no al argumento subsiguiente `b`.

## Do-Block Syntax for Function Arguments

Pasar funciones como argumentos a otras funciones es una técnica poderosa, pero la sintaxis para ello no siempre es conveniente. Tales llamadas son especialmente incómodas de escribir cuando el argumento de la función requiere múltiples líneas. Como ejemplo, considera llamar a [`map`](@ref) en una función con varios casos:

```julia
map(x->begin
           if x < 0 && iseven(x)
               return 0
           elseif x == 0
               return 1
           else
               return x
           end
       end,
    [A, B, C])
```

Julia proporciona una palabra reservada `do` para reescribir este código de manera más clara:

```julia
map([A, B, C]) do x
    if x < 0 && iseven(x)
        return 0
    elseif x == 0
        return 1
    else
        return x
    end
end
```

La sintaxis `do x` crea una función anónima con el argumento `x` y pasa la función anónima como el primer argumento a la función "externa" - [`map`](@ref) en este ejemplo. De manera similar, `do a,b` crearía una función anónima de dos argumentos. Ten en cuenta que `do (a,b)` crearía una función anónima de un argumento, cuyo argumento es una tupla que debe ser desestructurada. Un simple `do` declararía que lo que sigue es una función anónima de la forma `() -> ...`.

Cómo se inicializan estos argumentos depende de la función "externa"; aquí, [`map`](@ref) establecerá secuencialmente `x` en `A`, `B`, `C`, llamando a la función anónima en cada uno, tal como sucedería en la sintaxis `map(func, [A, B, C])`.

Esta sintaxis facilita el uso de funciones para extender el lenguaje de manera efectiva, ya que las llamadas se ven como bloques de código normales. Hay muchos usos posibles bastante diferentes de [`map`](@ref), como la gestión del estado del sistema. Por ejemplo, hay una versión de [`open`](@ref) que ejecuta código asegurando que el archivo abierto se cierre eventualmente:

```julia
open("outfile", "w") do io
    write(io, data)
end
```

Esto se logra mediante la siguiente definición:

```julia
function open(f::Function, args...)
    io = open(args...)
    try
        f(io)
    finally
        close(io)
    end
end
```

Aquí, [`open`](@ref) primero abre el archivo para escritura y luego pasa el flujo de salida resultante a la función anónima que definiste en el bloque `do ... end`. Después de que tu función salga, `4d61726b646f776e2e436f64652822222c20226f70656e2229_40726566` se asegurará de que el flujo se cierre correctamente, independientemente de si tu función salió normalmente o lanzó una excepción. (El constructo `try/finally` se describirá en [Control Flow](@ref).)

Con la sintaxis del bloque `do`, es útil consultar la documentación o la implementación para saber cómo se inicializan los argumentos de la función del usuario.

Un bloque `do`, como cualquier otra función interna, puede "capturar" variables de su ámbito envolvente. Por ejemplo, la variable `data` en el ejemplo anterior de `open...do` se captura del ámbito exterior. Las variables capturadas pueden crear desafíos de rendimiento, como se discute en [performance tips](@ref man-performance-captured).

## Function composition and piping

Las funciones en Julia se pueden combinar mediante la composición o el encadenamiento (piping) de ellas.

La composición de funciones es cuando combinas funciones y aplicas la composición resultante a los argumentos. Usas el operador de composición de funciones (`∘`) para componer las funciones, así que `(f ∘ g)(args...; kw...)` es lo mismo que `f(g(args...; kw...))`.

Puedes escribir el operador de composición en el REPL y en editores configurados adecuadamente usando `\circ<tab>`.

Por ejemplo, las funciones `sqrt` y `+` se pueden componer así:

```jldoctest
julia> (sqrt ∘ +)(3, 6)
3.0
```

Esto suma los números primero, luego encuentra la raíz cuadrada del resultado.

El siguiente ejemplo compone tres funciones y mapea el resultado sobre un array de cadenas:

```jldoctest
julia> map(first ∘ reverse ∘ uppercase, split("you can compose functions like this"))
6-element Vector{Char}:
 'U': ASCII/Unicode U+0055 (category Lu: Letter, uppercase)
 'N': ASCII/Unicode U+004E (category Lu: Letter, uppercase)
 'E': ASCII/Unicode U+0045 (category Lu: Letter, uppercase)
 'S': ASCII/Unicode U+0053 (category Lu: Letter, uppercase)
 'E': ASCII/Unicode U+0045 (category Lu: Letter, uppercase)
 'S': ASCII/Unicode U+0053 (category Lu: Letter, uppercase)
```

La encadenación de funciones (a veces llamada "piping" o "usar un pipe" para enviar datos a una función subsiguiente) es cuando aplicas una función a la salida de la función anterior:

```jldoctest
julia> 1:10 |> sum |> sqrt
7.416198487095663
```

Aquí, el total producido por `sum` se pasa a la función `sqrt`. La composición equivalente sería:

```jldoctest
julia> (sqrt ∘ sum)(1:10)
7.416198487095663
```

El operador de tubería también se puede usar con la difusión, como `.|>`, para proporcionar una combinación útil de la sintaxis de encadenamiento/tubería y la vectorización de puntos (descrito a continuación).

```jldoctest
julia> ["a", "list", "of", "strings"] .|> [uppercase, reverse, titlecase, length]
4-element Vector{Any}:
  "A"
  "tsil"
  "Of"
 7
```

Cuando se combinan tuberías con funciones anónimas, se deben usar paréntesis si las tuberías subsiguientes no deben ser analizadas como parte del cuerpo de la función anónima. Comparar:

```jldoctest
julia> 1:3 .|> (x -> x^2) |> sum |> sqrt
3.7416573867739413

julia> 1:3 .|> x -> x^2 |> sum |> sqrt
3-element Vector{Float64}:
 1.0
 2.0
 3.0
```

## [Dot Syntax for Vectorizing Functions](@id man-vectorized)

En los lenguajes de computación técnica, es común tener versiones "vectorizadas" de funciones, que simplemente aplican una función dada `f(x)` a cada elemento de un arreglo `A` para generar un nuevo arreglo a través de `f(A)`. Este tipo de sintaxis es conveniente para el procesamiento de datos, pero en otros lenguajes la vectorización también se requiere a menudo por razones de rendimiento: si los bucles son lentos, la versión "vectorizada" de una función puede llamar a código de biblioteca rápido escrito en un lenguaje de bajo nivel. En Julia, las funciones vectorizadas *no* son necesarias para el rendimiento, y de hecho, a menudo es beneficioso escribir tus propios bucles (ver [Performance Tips](@ref man-performance-tips)), pero aún pueden ser convenientes. Por lo tanto, *cualquier* función de Julia `f` puede aplicarse elemento a elemento a cualquier arreglo (u otra colección) con la sintaxis `f.(A)`. Por ejemplo, `sin` puede aplicarse a todos los elementos en el vector `A` de la siguiente manera:

```jldoctest
julia> A = [1.0, 2.0, 3.0]
3-element Vector{Float64}:
 1.0
 2.0
 3.0

julia> sin.(A)
3-element Vector{Float64}:
 0.8414709848078965
 0.9092974268256817
 0.1411200080598672
```

Por supuesto, puedes omitir el punto si escribes un método "vectorial" especializado de `f`, por ejemplo, a través de `f(A::AbstractArray) = map(f, A)`, y esto es tan eficiente como `f.(A)`. La ventaja de la sintaxis `f.(A)` es que no es necesario decidir de antemano qué funciones son vectorizables por el autor de la biblioteca.

Más generalmente, `f.(args...)` es en realidad equivalente a `broadcast(f, args...)`, lo que te permite operar en múltiples arreglos (incluso de diferentes formas), o una mezcla de arreglos y escalares (ver [Broadcasting](@ref)). Por ejemplo, si tienes `f(x, y) = 3x + 4y`, entonces `f.(pi, A)` devolverá un nuevo arreglo que consiste en `f(pi,a)` para cada `a` en `A`, y `f.(vector1, vector2)` devolverá un nuevo vector que consiste en `f(vector1[i], vector2[i])` para cada índice `i` (lanzando una excepción si los vectores tienen diferente longitud).

```jldoctest
julia> f(x, y) = 3x + 4y;

julia> A = [1.0, 2.0, 3.0];

julia> B = [4.0, 5.0, 6.0];

julia> f.(pi, A)
3-element Vector{Float64}:
 13.42477796076938
 17.42477796076938
 21.42477796076938

julia> f.(A, B)
3-element Vector{Float64}:
 19.0
 26.0
 33.0
```

Los argumentos de palabra clave no se transmiten, sino que se pasan simplemente a cada llamada de la función. Por ejemplo, `round.(x, digits=3)` es equivalente a `broadcast(x -> round(x, digits=3), x)`.

Además, las llamadas *anidadas* `f.(args...)` se *fusionan* en un solo bucle de `broadcast`. Por ejemplo, `sin.(cos.(X))` es equivalente a `broadcast(x -> sin(cos(x)), X)`, similar a `[sin(cos(x)) for x in X]`: solo hay un bucle sobre `X`, y se asigna un solo array para el resultado. [En contraste, `sin(cos(X))` en un lenguaje "vectorizado" típico primero asignaría un array temporal para `tmp=cos(X)`, y luego calcularía `sin(tmp)` en un bucle separado, asignando un segundo array.] Esta fusión de bucles no es una optimización del compilador que puede o no ocurrir, es una *garantía sintáctica* cada vez que se encuentran llamadas anidadas `f.(args...)`. Técnicamente, la fusión se detiene tan pronto como se encuentra una llamada a una función "no-dot"; por ejemplo, en `sin.(sort(cos.(X)))` los bucles de `sin` y `cos` no pueden fusionarse debido a la función `sort` intermedia.

Finalmente, la eficiencia máxima se logra típicamente cuando el array de salida de una operación vectorizada está *pre-asignado*, de modo que las llamadas repetidas no asignen nuevos arrays una y otra vez para los resultados (ver [Pre-allocating outputs](@ref)). Una sintaxis conveniente para esto es `X .= ...`, que es equivalente a `broadcast!(identity, X, ...)`, excepto que, como se mencionó anteriormente, el bucle `broadcast!` se fusiona con cualquier llamada "punto" anidada. Por ejemplo, `X .= sin.(Y)` es equivalente a `broadcast!(sin, X, Y)`, sobrescribiendo `X` con `sin.(Y)` en su lugar. Si el lado izquierdo es una expresión de indexación de array, por ejemplo, `X[begin+1:end] .= sin.(Y)`, entonces se traduce a `broadcast!` en una `view`, por ejemplo, `broadcast!(sin, view(X, firstindex(X)+1:lastindex(X)), Y)`, de modo que el lado izquierdo se actualiza en su lugar.

Dado que agregar puntos a muchas operaciones y llamadas a funciones en una expresión puede ser tedioso y llevar a un código que es difícil de leer, se proporciona la macro [`@.`](@ref @__dot__) para convertir *cada* llamada a función, operación y asignación en una expresión a la versión "con puntos".

```jldoctest
julia> Y = [1.0, 2.0, 3.0, 4.0];

julia> X = similar(Y); # pre-allocate output array

julia> @. X = sin(cos(Y)) # equivalent to X .= sin.(cos.(Y))
4-element Vector{Float64}:
  0.5143952585235492
 -0.4042391538522658
 -0.8360218615377305
 -0.6080830096407656
```

Los operadores binarios (o unarios) como `.+` se manejan con el mismo mecanismo: son equivalentes a llamadas de `broadcast` y se fusionan con otras llamadas "dot" anidadas. `X .+= Y`, etcétera, es equivalente a `X .= X .+ Y` y resulta en una asignación en el lugar fusionada; véase también [dot operators](@ref man-dot-operators).

También puedes combinar operaciones de punto con encadenamiento de funciones usando [`|>`](@ref), como en este ejemplo:

```jldoctest
julia> 1:5 .|> [x->x^2, inv, x->2*x, -, isodd]
5-element Vector{Real}:
    1
    0.5
    6
   -4
 true
```

Todas las funciones en la difusión fusionada se llaman siempre para cada elemento del resultado. Así, `X .+ σ .* randn.()` añadirá una máscara de valores aleatorios independientes e idénticamente muestreados a cada elemento del array `X`, pero `X .+ σ .* randn()` añadirá la *misma* muestra aleatoria a cada elemento. En casos donde el cálculo fusionado es constante a lo largo de uno o más ejes de la iteración de difusión, puede ser posible aprovechar un intercambio espacio-temporal y asignar valores intermedios para reducir el número de cálculos. Ver más en [performance tips](@ref man-performance-unfuse).

## Further Reading

Debemos mencionar aquí que esto está lejos de ser una imagen completa de la definición de funciones. Julia tiene un sistema de tipos sofisticado y permite el despacho múltiple en los tipos de argumentos. Ninguno de los ejemplos dados aquí proporciona anotaciones de tipo en sus argumentos, lo que significa que son aplicables a todos los tipos de argumentos. El sistema de tipos se describe en [Types](@ref man-types) y la definición de una función en términos de métodos elegidos por el despacho múltiple en los tipos de argumentos en tiempo de ejecución se describe en [Methods](@ref).
