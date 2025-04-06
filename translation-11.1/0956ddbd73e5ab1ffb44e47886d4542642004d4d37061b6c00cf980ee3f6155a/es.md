# Metaprogramming

El legado más fuerte de Lisp en el lenguaje Julia es su soporte para metaprogramación. Al igual que Lisp, Julia representa su propio código como una estructura de datos del propio lenguaje. Dado que el código está representado por objetos que pueden ser creados y manipulados desde dentro del lenguaje, es posible que un programa transforme y genere su propio código. Esto permite una generación de código sofisticada sin pasos de construcción adicionales, y también permite macros verdaderas al estilo Lisp que operan al nivel de [abstract syntax trees](https://en.wikipedia.org/wiki/Abstract_syntax_tree). En contraste, los sistemas de "macro" de preprocesador, como los de C y C++, realizan manipulación y sustitución textual antes de que ocurra cualquier análisis o interpretación real. Debido a que todos los tipos de datos y el código en Julia están representados por estructuras de datos de Julia, potentes [reflection](https://en.wikipedia.org/wiki/Reflection_%28computer_programming%29) capacidades están disponibles para explorar los internos de un programa y sus tipos, al igual que cualquier otro dato.

!!! warning
    La metaprogramación es una herramienta poderosa, pero introduce complejidad que puede hacer que el código sea más difícil de entender. Por ejemplo, puede ser sorprendentemente difícil obtener las reglas de alcance correctas. La metaprogramación debería utilizarse típicamente solo cuando otros enfoques como [higher order functions](@ref man-anonymous-functions) y [closures](https://en.wikipedia.org/wiki/Closure_(computer_programming)) no pueden aplicarse.

    `eval` y la definición de nuevas macros deben usarse típicamente como último recurso. Casi nunca es una buena idea usar `Meta.parse` o convertir una cadena arbitraria en código Julia. Para manipular código Julia, utiliza directamente la estructura de datos `Expr` para evitar la complejidad de cómo se analiza la sintaxis de Julia.

    Los mejores usos de la metaprogramación a menudo implementan la mayor parte de su funcionalidad en funciones auxiliares en tiempo de ejecución, esforzándose por minimizar la cantidad de código que generan.


## Program representation

Cada programa de Julia comienza su vida como una cadena:

```jldoctest prog
julia> prog = "1 + 1"
"1 + 1"
```

**¿Qué sucede después?**

El siguiente paso es [parse](https://en.wikipedia.org/wiki/Parsing#Computer_languages) cada cadena en un objeto llamado expresión, representado por el tipo de Julia [`Expr`](@ref):

```jldoctest prog
julia> ex1 = Meta.parse(prog)
:(1 + 1)

julia> typeof(ex1)
Expr
```

Los objetos `Expr` contienen dos partes:

  * un [`Symbol`](@ref) identificando el tipo de expresión. Un símbolo es un [interned string](https://en.wikipedia.org/wiki/String_interning) identificador (más discusión a continuación).

```jldoctest prog
julia> ex1.head
:call
```

  * los argumentos de expresión, que pueden ser símbolos, otras expresiones o valores literales:

```jldoctest prog
julia> ex1.args
3-element Vector{Any}:
  :+
 1
 1
```

Las expresiones también se pueden construir directamente en [prefix notation](https://en.wikipedia.org/wiki/Polish_notation):

```jldoctest prog
julia> ex2 = Expr(:call, :+, 1, 1)
:(1 + 1)
```

Las dos expresiones construidas arriba – mediante análisis y mediante construcción directa – son equivalentes:

```jldoctest prog
julia> ex1 == ex2
true
```

**El punto clave aquí es que el código de Julia se representa internamente como una estructura de datos que es accesible desde el propio lenguaje.**

La función [`dump`](@ref) proporciona una visualización indentada y anotada de los objetos `Expr`:

```jldoctest prog
julia> dump(ex2)
Expr
  head: Symbol call
  args: Array{Any}((3,))
    1: Symbol +
    2: Int64 1
    3: Int64 1
```

Los objetos `Expr` también pueden estar anidados:

```jldoctest ex3
julia> ex3 = Meta.parse("(4 + 4) / 2")
:((4 + 4) / 2)
```

Otra forma de ver expresiones es con `Meta.show_sexpr`, que muestra la forma [S-expression](https://en.wikipedia.org/wiki/S-expression) de un `Expr` dado, que puede parecer muy familiar para los usuarios de Lisp. Aquí hay un ejemplo que ilustra la visualización en un `Expr` anidado:

```jldoctest ex3
julia> Meta.show_sexpr(ex3)
(:call, :/, (:call, :+, 4, 4), 2)
```

### Symbols

El `:` carácter tiene dos propósitos sintácticos en Julia. La primera forma crea un [`Symbol`](@ref), un [interned string](https://en.wikipedia.org/wiki/String_interning) utilizado como uno de los bloques de construcción de expresiones, a partir de identificadores válidos:

```jldoctest
julia> s = :foo
:foo

julia> typeof(s)
Symbol
```

El constructor [`Symbol`](@ref) acepta cualquier número de argumentos y crea un nuevo símbolo concatenando sus representaciones en cadena:

```jldoctest
julia> :foo === Symbol("foo")
true

julia> Symbol("1foo") # `:1foo` would not work, as `1foo` is not a valid identifier
Symbol("1foo")

julia> Symbol("func",10)
:func10

julia> Symbol(:var,'_',"sym")
:var_sym
```

En el contexto de una expresión, se utilizan símbolos para indicar el acceso a variables; cuando se evalúa una expresión, un símbolo se reemplaza con el valor asociado a ese símbolo en el [scope](@ref scope-of-variables).

A veces se necesitan paréntesis adicionales alrededor del argumento a `:` para evitar ambigüedad en el análisis:

```jldoctest
julia> :(:)
:(:)

julia> :(::)
:(::)
```

## Expressions and evaluation

### Quoting

El segundo propósito sintáctico del carácter `:` es crear objetos de expresión sin usar el constructor explícito [`Expr`](@ref). Esto se conoce como *citación*. El carácter `:`, seguido de paréntesis emparejados alrededor de una única declaración de código Julia, produce un objeto `Expr` basado en el código encerrado. Aquí hay un ejemplo de la forma corta utilizada para citar una expresión aritmética:

```jldoctest
julia> ex = :(a+b*c+1)
:(a + b * c + 1)

julia> typeof(ex)
Expr
```

(para ver la estructura de esta expresión, intenta `ex.head` y `ex.args`, o usa [`dump`](@ref) como arriba o [`Meta.@dump`](@ref))

Tenga en cuenta que se pueden construir expresiones equivalentes utilizando [`Meta.parse`](@ref) o la forma directa `Expr`:

```jldoctest
julia>      :(a + b*c + 1)       ==
       Meta.parse("a + b*c + 1") ==
       Expr(:call, :+, :a, Expr(:call, :*, :b, :c), 1)
true
```

Las expresiones proporcionadas por el analizador generalmente solo tienen símbolos, otras expresiones y valores literales como sus argumentos, mientras que las expresiones construidas por código Julia pueden tener valores arbitrarios en tiempo de ejecución sin formas literales como argumentos. En este ejemplo específico, `+` y `a` son símbolos, `*(b,c)` es una subexpresión, y `1` es un entero con signo de 64 bits literal.

Hay una segunda forma sintáctica de citar para múltiples expresiones: bloques de código encerrados en `quote ... end`.

```jldoctest
julia> ex = quote
           x = 1
           y = 2
           x + y
       end
quote
    #= none:2 =#
    x = 1
    #= none:3 =#
    y = 2
    #= none:4 =#
    x + y
end

julia> typeof(ex)
Expr
```

### [Interpolation](@id man-expression-interpolation)

La construcción directa de objetos [`Expr`](@ref) con argumentos de valor es poderosa, pero los constructores `Expr` pueden ser tediosos en comparación con la sintaxis "normal" de Julia. Como alternativa, Julia permite la *interpolación* de literales o expresiones en expresiones citadas. La interpolación se indica con un prefijo `$`.

En este ejemplo, el valor de la variable `a` está interpolado:

```jldoctest interp1
julia> a = 1;

julia> ex = :($a + b)
:(1 + b)
```

Interpolar en una expresión no citada no es compatible y causará un error en tiempo de compilación:

```jldoctest interp1
julia> $a + b
ERROR: syntax: "$" expression outside quote
```

En este ejemplo, la tupla `(1,2,3)` se interpola como una expresión en una prueba condicional:

```jldoctest interp1
julia> ex = :(a in $:((1,2,3)) )
:(a in (1, 2, 3))
```

El uso de `$` para la interpolación de expresiones es intencionalmente reminiscentemente de [string interpolation](@ref string-interpolation) y [command interpolation](@ref command-interpolation). La interpolación de expresiones permite la construcción programática conveniente y legible de expresiones complejas en Julia.

### Splatting interpolation

Tenga en cuenta que la sintaxis de interpolación `$` permite insertar solo una única expresión en una expresión envolvente. Ocasionalmente, tiene un arreglo de expresiones y necesita que todas se conviertan en argumentos de la expresión circundante. Esto se puede hacer con la sintaxis `$(xs...)`. Por ejemplo, el siguiente código genera una llamada a una función donde el número de argumentos se determina programáticamente:

```jldoctest interp1
julia> args = [:x, :y, :z];

julia> :(f(1, $(args...)))
:(f(1, x, y, z))
```

### Nested quote

Naturalmente, es posible que las expresiones de cita contengan otras expresiones de cita. Entender cómo funciona la interpolación en estos casos puede ser un poco complicado. Considera este ejemplo:

```jldoctest interp1
julia> x = :(1 + 2);

julia> e = quote quote $x end end
quote
    #= none:1 =#
    $(Expr(:quote, quote
    #= none:1 =#
    $(Expr(:$, :x))
end))
end
```

Tenga en cuenta que el resultado contiene `$x`, lo que significa que `x` aún no ha sido evaluado. En otras palabras, la expresión `$` "pertenece" a la expresión de comillas internas, y por lo tanto su argumento solo se evalúa cuando la expresión de comillas internas es:

```jldoctest interp1
julia> eval(e)
quote
    #= none:1 =#
    1 + 2
end
```

Sin embargo, la expresión `quote` externa puede interpolar valores dentro del `$` en la cita interna. Esto se hace con múltiples `$`:

```jldoctest interp1
julia> e = quote quote $$x end end
quote
    #= none:1 =#
    $(Expr(:quote, quote
    #= none:1 =#
    $(Expr(:$, :(1 + 2)))
end))
end
```

Nota que `(1 + 2)` ahora aparece en el resultado en lugar del símbolo `x`. Evaluar esta expresión da como resultado un `3` interpolado:

```jldoctest interp1
julia> eval(e)
quote
    #= none:1 =#
    3
end
```

La intuición detrás de este comportamiento es que `x` se evalúa una vez por cada `$`: un `$` funciona de manera similar a `eval(:x)`, dando el valor de `x`, mientras que dos `$` hacen lo equivalente a `eval(eval(:x))`.

### [QuoteNode](@id man-quote-node)

The usual representation of a `quote` form in an AST is an [`Expr`](@ref) with head `:quote`:

```jldoctest interp1
julia> dump(Meta.parse(":(1+2)"))
Expr
  head: Symbol quote
  args: Array{Any}((1,))
    1: Expr
      head: Symbol call
      args: Array{Any}((3,))
        1: Symbol +
        2: Int64 1
        3: Int64 2
```

Como hemos visto, tales expresiones admiten interpolación con `$`. Sin embargo, en algunas situaciones es necesario citar código *sin* realizar interpolación. Este tipo de cita aún no tiene sintaxis, pero se representa internamente como un objeto del tipo `QuoteNode`:

```jldoctest interp1
julia> eval(Meta.quot(Expr(:$, :(1+2))))
3

julia> eval(QuoteNode(Expr(:$, :(1+2))))
:($(Expr(:$, :(1 + 2))))
```

El analizador produce `QuoteNode`s para elementos citados simples como símbolos:

```jldoctest interp1
julia> dump(Meta.parse(":x"))
QuoteNode
  value: Symbol x
```

`QuoteNode` también se puede utilizar para ciertas tareas avanzadas de metaprogramación.

### Evaluating expressions

Dado un objeto de expresión, uno puede hacer que Julia lo evalúe (ejecute) en el ámbito global usando [`eval`](@ref):

```jldoctest interp1
julia> ex1 = :(1 + 2)
:(1 + 2)

julia> eval(ex1)
3

julia> ex = :(a + b)
:(a + b)

julia> eval(ex)
ERROR: UndefVarError: `b` not defined in `Main`
[...]

julia> a = 1; b = 2;

julia> eval(ex)
3
```

Cada [module](@ref modules) tiene su propia función [`eval`](@ref) que evalúa expresiones en su ámbito global. Las expresiones pasadas a `4d61726b646f776e2e436f64652822222c20226576616c2229_40726566` no se limitan a devolver valores; también pueden tener efectos secundarios que alteran el estado del entorno del módulo que las contiene:

```jldoctest
julia> ex = :(x = 1)
:(x = 1)

julia> x
ERROR: UndefVarError: `x` not defined in `Main`

julia> eval(ex)
1

julia> x
1
```

Aquí, la evaluación de un objeto de expresión provoca que se asigne un valor a la variable global `x`.

Dado que las expresiones son solo objetos `Expr` que se pueden construir programáticamente y luego evaluar, es posible generar dinámicamente código arbitrario que luego se puede ejecutar utilizando [`eval`](@ref). Aquí hay un ejemplo simple:

```julia-repl
julia> a = 1;

julia> ex = Expr(:call, :+, a, :b)
:(1 + b)

julia> a = 0; b = 2;

julia> eval(ex)
3
```

El valor de `a` se utiliza para construir la expresión `ex` que aplica la función `+` al valor 1 y a la variable `b`. Tenga en cuenta la importante distinción entre la forma en que se utilizan `a` y `b`:

  * El valor de la *variable* `a` en el momento de la construcción de la expresión se utiliza como un valor inmediato en la expresión. Por lo tanto, el valor de `a` cuando se evalúa la expresión ya no importa: el valor en la expresión ya es `1`, independientemente de cuál sea el valor de `a`.
  * Por otro lado, el *símbolo* `:b` se utiliza en la construcción de expresiones, por lo que el valor de la variable `b` en ese momento es irrelevante; `:b` es solo un símbolo y la variable `b` ni siquiera necesita estar definida. Sin embargo, en el momento de la evaluación de la expresión, el valor del símbolo `:b` se resuelve buscando el valor de la variable `b`.

### Functions on `Expr`essions

As hinted above, one extremely useful feature of Julia is the capability to generate and manipulate Julia code within Julia itself. We have already seen one example of a function returning [`Expr`](@ref) objects: the [`Meta.parse`](@ref) function, which takes a string of Julia code and returns the corresponding `Expr`. A function can also take one or more `Expr` objects as arguments, and return another `Expr`. Here is a simple, motivating example:

```jldoctest
julia> function math_expr(op, op1, op2)
           expr = Expr(:call, op, op1, op2)
           return expr
       end
math_expr (generic function with 1 method)

julia>  ex = math_expr(:+, 1, Expr(:call, :*, 4, 5))
:(1 + 4 * 5)

julia> eval(ex)
21
```

Como otro ejemplo, aquí hay una función que duplica cualquier argumento numérico, pero deja las expresiones solas:

```jldoctest
julia> function make_expr2(op, opr1, opr2)
           opr1f, opr2f = map(x -> isa(x, Number) ? 2*x : x, (opr1, opr2))
           retexpr = Expr(:call, op, opr1f, opr2f)
           return retexpr
       end
make_expr2 (generic function with 1 method)

julia> make_expr2(:+, 1, 2)
:(2 + 4)

julia> ex = make_expr2(:+, 1, Expr(:call, :*, 5, 8))
:(2 + 5 * 8)

julia> eval(ex)
42
```

## [Macros](@id man-macros)

Los macros proporcionan un mecanismo para incluir código generado en el cuerpo final de un programa. Un macro mapea una tupla de argumentos a una *expresión* devuelta, y la expresión resultante se compila directamente en lugar de requerir una llamada en tiempo de ejecución [`eval`](@ref). Los argumentos del macro pueden incluir expresiones, valores literales y símbolos.

### Basics

Aquí hay un macro extraordinariamente simple:

```jldoctest sayhello
julia> macro sayhello()
           return :( println("Hello, world!") )
       end
@sayhello (macro with 1 method)
```

Los macros tienen un carácter dedicado en la sintaxis de Julia: el `@` (signo de arroba), seguido del nombre único declarado en un bloque `macro NAME ... end`. En este ejemplo, el compilador reemplazará todas las instancias de `@sayhello` con:

```julia
:( println("Hello, world!") )
```

Cuando se ingresa `@sayhello` en el REPL, la expresión se ejecuta inmediatamente, por lo que solo vemos el resultado de la evaluación:

```jldoctest sayhello
julia> @sayhello()
Hello, world!
```

Ahora, considera un macro un poco más complejo:

```jldoctest sayhello2
julia> macro sayhello(name)
           return :( println("Hello, ", $name) )
       end
@sayhello (macro with 1 method)
```

Este macro toma un argumento: `name`. Cuando se encuentra `@sayhello`, la expresión entre comillas se *expande* para interpolar el valor del argumento en la expresión final:

```jldoctest sayhello2
julia> @sayhello("human")
Hello, human
```

Podemos ver la expresión de retorno citada utilizando la función [`macroexpand`](@ref) (**nota importante:** esta es una herramienta extremadamente útil para depurar macros):

```julia-repl sayhello2
julia> ex = macroexpand(Main, :(@sayhello("human")) )
:(Main.println("Hello, ", "human"))

julia> typeof(ex)
Expr
```

Podemos ver que el literal `"human"` ha sido interpolado en la expresión.

También existe un macro [`@macroexpand`](@ref) que es quizás un poco más conveniente que la función `macroexpand`:

```jldoctest sayhello2
julia> @macroexpand @sayhello "human"
:(println("Hello, ", "human"))
```

### Hold up: why macros?

Ya hemos visto una función `f(::Expr...) -> Expr` en una sección anterior. De hecho, [`macroexpand`](@ref) también es una función así. Entonces, ¿por qué existen los macros?

Los macros son necesarios porque se ejecutan cuando se analiza el código, por lo tanto, los macros permiten al programador generar e incluir fragmentos de código personalizado *antes* de que se ejecute el programa completo. Para ilustrar la diferencia, considera el siguiente ejemplo:

```julia-repl whymacros
julia> macro twostep(arg)
           println("I execute at parse time. The argument is: ", arg)
           return :(println("I execute at runtime. The argument is: ", $arg))
       end
@twostep (macro with 1 method)

julia> ex = macroexpand(Main, :(@twostep :(1, 2, 3)) );
I execute at parse time. The argument is: :((1, 2, 3))
```

La primera llamada a [`println`](@ref) se ejecuta cuando se llama a [`macroexpand`](@ref). La expresión resultante contiene *solo* el segundo `println`:

```julia-repl whymacros
julia> typeof(ex)
Expr

julia> ex
:(println("I execute at runtime. The argument is: ", $(Expr(:copyast, :($(QuoteNode(:((1, 2, 3)))))))))

julia> eval(ex)
I execute at runtime. The argument is: (1, 2, 3)
```

### Macro invocation

Los macros se invocan con la siguiente sintaxis general:

```julia
@name expr1 expr2 ...
@name(expr1, expr2, ...)
```

Tenga en cuenta el distintivo `@` antes del nombre de la macro y la falta de comas entre las expresiones de argumento en la primera forma, y la falta de espacio en blanco después de `@name` en la segunda forma. Los dos estilos no deben mezclarse. Por ejemplo, la siguiente sintaxis es diferente de los ejemplos anteriores; pasa la tupla `(expr1, expr2, ...)` como un argumento a la macro:

```julia
@name (expr1, expr2, ...)
```

Una forma alternativa de invocar un macro sobre un literal de arreglo (o comprensión) es yuxtaponer ambos sin usar paréntesis. En este caso, el arreglo será la única expresión alimentada al macro. La siguiente sintaxis es equivalente (y diferente de `@name [a b] * v`):

```julia
@name[a b] * v
@name([a b]) * v
```

Es importante enfatizar que los macros reciben sus argumentos como expresiones, literales o símbolos. Una forma de explorar los argumentos de un macro es llamar a la función [`show`](@ref) dentro del cuerpo del macro:

```jldoctest
julia> macro showarg(x)
           show(x)
           # ... remainder of macro, returning an expression
       end
@showarg (macro with 1 method)

julia> @showarg(a)
:a

julia> @showarg(1+1)
:(1 + 1)

julia> @showarg(println("Yo!"))
:(println("Yo!"))

julia> @showarg(1)        # Numeric literal
1

julia> @showarg("Yo!")    # String literal
"Yo!"

julia> @showarg("Yo! $("hello")")    # String with interpolation is an Expr rather than a String
:("Yo! $("hello")")
```

Además de la lista de argumentos dada, a cada macro se le pasan argumentos adicionales llamados `__source__` y `__module__`.

El argumento `__source__` proporciona información (en forma de un objeto `LineNumberNode`) sobre la ubicación del analizador del signo `@` a partir de la invocación de la macro. Esto permite que las macros incluyan mejor información de diagnóstico de errores, y se utiliza comúnmente en registros, macros de análisis de cadenas y documentación, por ejemplo, así como para implementar las macros [`@__LINE__`](@ref), [`@__FILE__`](@ref), y [`@__DIR__`](@ref).

La información de ubicación se puede acceder haciendo referencia a `__source__.line` y `__source__.file`:

```jldoctest
julia> macro __LOCATION__(); return QuoteNode(__source__); end
@__LOCATION__ (macro with 1 method)

julia> dump(
            @__LOCATION__(
       ))
LineNumberNode
  line: Int64 2
  file: Symbol none
```

El argumento `__module__` proporciona información (en forma de un objeto `Module`) sobre el contexto de expansión de la invocación de la macro. Esto permite a las macros buscar información contextual, como vinculaciones existentes, o insertar el valor como un argumento adicional a una llamada de función en tiempo de ejecución que realiza auto-reflexión en el módulo actual.

### Building an advanced macro

Aquí hay una definición simplificada del macro [`@assert`](@ref) de Julia:

```jldoctest building
julia> macro assert(ex)
           return :( $ex ? nothing : throw(AssertionError($(string(ex)))) )
       end
@assert (macro with 1 method)
```

Este macro se puede usar de la siguiente manera:

```jldoctest building
julia> @assert 1 == 1.0

julia> @assert 1 == 0
ERROR: AssertionError: 1 == 0
```

En lugar de la sintaxis escrita, la llamada a la macro se expande en tiempo de análisis a su resultado devuelto. Esto es equivalente a escribir:

```julia
1 == 1.0 ? nothing : throw(AssertionError("1 == 1.0"))
1 == 0 ? nothing : throw(AssertionError("1 == 0"))
```

Es decir, en la primera llamada, la expresión `:(1 == 1.0)` se inserta en el espacio de condición de prueba, mientras que el valor de `string(:(1 == 1.0))` se inserta en el espacio del mensaje de aserción. La expresión completa, así construida, se coloca en el árbol de sintaxis donde ocurre la llamada al macro `@assert`. Luego, en el momento de la ejecución, si la expresión de prueba evalúa a verdadero, se devuelve [`nothing`](@ref), mientras que si la prueba es falsa, se genera un error que indica la expresión afirmada que fue falsa. Observe que no sería posible escribir esto como una función, ya que solo está disponible el *valor* de la condición y sería imposible mostrar la expresión que la calculó en el mensaje de error.

La definición actual de `@assert` en Julia Base es más complicada. Permite al usuario especificar opcionalmente su propio mensaje de error, en lugar de simplemente imprimir la expresión fallida. Al igual que en las funciones con un número variable de argumentos ([Varargs Functions](@ref)), esto se especifica con una elipsis después del último argumento:

```jldoctest assert2
julia> macro assert(ex, msgs...)
           msg_body = isempty(msgs) ? ex : msgs[1]
           msg = string(msg_body)
           return :($ex ? nothing : throw(AssertionError($msg)))
       end
@assert (macro with 1 method)
```

Ahora `@assert` tiene dos modos de operación, dependiendo del número de argumentos que recibe. Si solo hay un argumento, la tupla de expresiones capturadas por `msgs` estará vacía y se comportará de la misma manera que la definición más simple anterior. Pero ahora, si el usuario especifica un segundo argumento, se imprimirá en el cuerpo del mensaje en lugar de la expresión que falla. Puedes inspeccionar el resultado de una expansión de macro con la macro acertadamente llamada [`@macroexpand`](@ref):

```julia-repl assert2
julia> @macroexpand @assert a == b
:(if Main.a == Main.b
        Main.nothing
    else
        Main.throw(Main.AssertionError("a == b"))
    end)

julia> @macroexpand @assert a==b "a should equal b!"
:(if Main.a == Main.b
        Main.nothing
    else
        Main.throw(Main.AssertionError("a should equal b!"))
    end)
```

Hay otro caso que el macro `@assert` maneja: ¿qué pasa si, además de imprimir "a debería ser igual a b", queremos imprimir sus valores? Uno podría intentar ingenuamente usar interpolación de cadenas en el mensaje personalizado, por ejemplo, `@assert a==b "a ($a) debería ser igual a b ($b)!"`, pero esto no funcionará como se esperaba con el macro anterior. ¿Puedes ver por qué? Recuerda de [string interpolation](@ref string-interpolation) que una cadena interpolada se reescribe como una llamada a [`string`](@ref). Compara:

```jldoctest
julia> typeof(:("a should equal b"))
String

julia> typeof(:("a ($a) should equal b ($b)!"))
Expr

julia> dump(:("a ($a) should equal b ($b)!"))
Expr
  head: Symbol string
  args: Array{Any}((5,))
    1: String "a ("
    2: Symbol a
    3: String ") should equal b ("
    4: Symbol b
    5: String ")!"
```

Así que ahora, en lugar de obtener una cadena simple en `msg_body`, la macro está recibiendo una expresión completa que necesitará ser evaluada para mostrarse como se espera. Esto se puede insertar directamente en la expresión devuelta como un argumento a la llamada [`string`](@ref); consulta [`error.jl`](https://github.com/JuliaLang/julia/blob/master/base/error.jl) para la implementación completa.

El macro `@assert` hace un gran uso de la inserción en expresiones citadas para simplificar la manipulación de expresiones dentro del cuerpo del macro.

### Hygiene

Un problema que surge en macros más complejas es el de [hygiene](https://en.wikipedia.org/wiki/Hygienic_macro). En resumen, las macros deben asegurarse de que las variables que introducen en sus expresiones devueltas no choquen accidentalmente con las variables existentes en el código circundante en el que se expanden. Por el contrario, se espera que las expresiones que se pasan a una macro como argumentos se evalúen en el contexto del código circundante, interactuando y modificando las variables existentes. Otra preocupación surge del hecho de que una macro puede ser llamada en un módulo diferente del que fue definida. En este caso, necesitamos asegurarnos de que todas las variables globales se resuelvan al módulo correcto. Julia ya tiene una gran ventaja sobre los lenguajes con expansión de macros textual (como C) en que solo necesita considerar la expresión devuelta. Todas las otras variables (como `msg` en `@assert` arriba) siguen el [normal scoping block behavior](@ref scope-of-variables).

Para demostrar estos problemas, consideremos escribir un macro `@time` que toma una expresión como su argumento, registra el tiempo, evalúa la expresión, registra el tiempo nuevamente, imprime la diferencia entre los tiempos antes y después, y luego tiene el valor de la expresión como su valor final. El macro podría verse así:

```julia
macro time(ex)
    return quote
        local t0 = time_ns()
        local val = $ex
        local t1 = time_ns()
        println("elapsed time: ", (t1-t0)/1e9, " seconds")
        val
    end
end
```

Aquí, queremos que `t0`, `t1` y `val` sean variables temporales privadas, y queremos que `time_ns` se refiera a la función [`time_ns`](@ref) en Julia Base, no a ninguna variable `time_ns` que el usuario pueda tener (lo mismo se aplica a `println`). Imagina los problemas que podrían ocurrir si la expresión del usuario `ex` también contenía asignaciones a una variable llamada `t0`, o definía su propia variable `time_ns`. Podríamos obtener errores o un comportamiento misteriosamente incorrecto.

El expansor de macros de Julia resuelve estos problemas de la siguiente manera. Primero, las variables dentro de un resultado de macro se clasifican como locales o globales. Una variable se considera local si se le asigna (y no se declara global), se declara local o se utiliza como nombre de argumento de función. De lo contrario, se considera global. Las variables locales se renombran para ser únicas (utilizando la función [`gensym`](@ref), que genera nuevos símbolos), y las variables globales se resuelven dentro del entorno de definición de la macro. Por lo tanto, ambas preocupaciones anteriores se manejan; las locales de la macro no entrarán en conflicto con ninguna variable del usuario, y `time_ns` y `println` se referirán a las definiciones de Julia Base.

Sin embargo, queda un problema. Considera el siguiente uso de este macro:

```julia
module MyModule
import Base.@time

time_ns() = ... # compute something

@time time_ns()
end
```

Aquí la expresión del usuario `ex` es una llamada a `time_ns`, pero no la misma función `time_ns` que utiliza el macro. Se refiere claramente a `MyModule.time_ns`. Por lo tanto, debemos asegurarnos de que el código en `ex` se resuelva en el entorno de llamada del macro. Esto se hace "escapando" la expresión con [`esc`](@ref):

```julia
macro time(ex)
    ...
    local val = $(esc(ex))
    ...
end
```

Una expresión envuelta de esta manera se deja sola por el expansor de macros y simplemente se pega en la salida tal cual. Por lo tanto, se resolverá en el entorno de llamada de la macro.

Este mecanismo de escape se puede utilizar para "violar" la higiene cuando sea necesario, con el fin de introducir o manipular variables de usuario. Por ejemplo, el siguiente macro establece `x` en cero en el entorno de llamada:

```jldoctest
julia> macro zerox()
           return esc(:(x = 0))
       end
@zerox (macro with 1 method)

julia> function foo()
           x = 1
           @zerox
           return x # is zero
       end
foo (generic function with 1 method)

julia> foo()
0
```

Este tipo de manipulación de variables debe usarse con prudencia, pero ocasionalmente es bastante útil.

Obtener las reglas de higiene correctas puede ser un desafío formidable. Antes de usar un macro, es posible que desees considerar si un cierre de función sería suficiente. Otra estrategia útil es diferir tanto trabajo como sea posible a tiempo de ejecución. Por ejemplo, muchos macros simplemente envuelven sus argumentos en un `QuoteNode` u otro [`Expr`](@ref) similar. Algunos ejemplos de esto incluyen `@task body`, que simplemente devuelve `schedule(Task(() -> $body))`, y `@eval expr`, que simplemente devuelve `eval(QuoteNode(expr))`.

Para demostrar, podríamos reescribir el ejemplo de `@time` anterior como:

```julia
macro time(expr)
    return :(timeit(() -> $(esc(expr))))
end
function timeit(f)
    t0 = time_ns()
    val = f()
    t1 = time_ns()
    println("elapsed time: ", (t1-t0)/1e9, " seconds")
    return val
end
```

Sin embargo, no hacemos esto por una buena razón: envolver el `expr` en un nuevo bloque de ámbito (la función anónima) también cambia ligeramente el significado de la expresión (el ámbito de cualquier variable en ella), mientras que queremos que `@time` sea utilizable con el mínimo impacto en el código envuelto.

### Macros and dispatch

Los macros, al igual que las funciones de Julia, son genéricos. Esto significa que también pueden tener múltiples definiciones de métodos, gracias al despacho múltiple:

```jldoctest macromethods
julia> macro m end
@m (macro with 0 methods)

julia> macro m(args...)
           println("$(length(args)) arguments")
       end
@m (macro with 1 method)

julia> macro m(x,y)
           println("Two arguments")
       end
@m (macro with 2 methods)

julia> @m "asd"
1 arguments

julia> @m 1 2
Two arguments
```

Sin embargo, uno debe tener en cuenta que el despacho macro se basa en los tipos de AST que se entregan al macro, no en los tipos a los que el AST se evalúa en tiempo de ejecución:

```jldoctest macromethods
julia> macro m(::Int)
           println("An Integer")
       end
@m (macro with 3 methods)

julia> @m 2
An Integer

julia> x = 2
2

julia> @m x
1 arguments
```

## Code Generation

Cuando se requiere una cantidad significativa de código repetitivo estándar, es común generarlo programáticamente para evitar redundancias. En la mayoría de los lenguajes, esto requiere un paso de construcción adicional y un programa separado para generar el código repetitivo. En Julia, la interpolación de expresiones y [`eval`](@ref) permiten que dicha generación de código tenga lugar en el curso normal de la ejecución del programa. Por ejemplo, considere el siguiente tipo personalizado.

```jldoctest mynumber-codegen
struct MyNumber
    x::Float64
end
# output

```

para el cual queremos agregar una serie de métodos. Podemos hacer esto programáticamente en el siguiente bucle:

```jldoctest mynumber-codegen
for op = (:sin, :cos, :tan, :log, :exp)
    eval(quote
        Base.$op(a::MyNumber) = MyNumber($op(a.x))
    end)
end
# output

```

y ahora podemos usar esas funciones con nuestro tipo personalizado:

```jldoctest mynumber-codegen
julia> x = MyNumber(π)
MyNumber(3.141592653589793)

julia> sin(x)
MyNumber(1.2246467991473532e-16)

julia> cos(x)
MyNumber(-1.0)
```

De esta manera, Julia actúa como su propio [preprocessor](https://en.wikipedia.org/wiki/Preprocessor), y permite la generación de código desde dentro del lenguaje. El código anterior podría escribirse de manera un poco más concisa utilizando la forma de cita con prefijo `:`:

```julia
for op = (:sin, :cos, :tan, :log, :exp)
    eval(:(Base.$op(a::MyNumber) = MyNumber($op(a.x))))
end
```

Este tipo de generación de código en el mismo lenguaje, sin embargo, utilizando el patrón `eval(quote(...))`, es lo suficientemente común que Julia viene con un macro para abreviar este patrón:

```julia
for op = (:sin, :cos, :tan, :log, :exp)
    @eval Base.$op(a::MyNumber) = MyNumber($op(a.x))
end
```

El macro [`@eval`](@ref) reescribe esta llamada para ser precisamente equivalente a las versiones más largas anteriores. Para bloques más largos de código generado, el argumento de expresión dado a `4d61726b646f776e2e436f64652822222c2022406576616c2229_40726566` puede ser un bloque:

```julia
@eval begin
    # multiple lines
end
```

## [Non-Standard String Literals](@id meta-non-standard-string-literals)

Recuerda de [Strings](@ref non-standard-string-literals) que los literales de cadena precedidos por un identificador se llaman literales de cadena no estándar, y pueden tener diferentes semánticas que los literales de cadena sin prefijo. Por ejemplo:

  * `r"^\s*(?:#|$)"` produce un [regular expression object](@ref man-regex-literals) en lugar de una cadena.
  * `b"DATA\xff\u2200"` es un [byte array literal](@ref man-byte-array-literals) para `[68,65,84,65,255,226,136,128]`.

Quizás sorprendentemente, estos comportamientos no están codificados en el analizador o compilador de Julia. En cambio, son comportamientos personalizados proporcionados por un mecanismo general que cualquiera puede usar: los literales de cadena con prefijo se analizan como llamadas a macros con nombres especiales. Por ejemplo, la macro de expresión regular es solo lo siguiente:

```julia
macro r_str(p)
    Regex(p)
end
```

Eso es todo. Este macro dice que el contenido literal de la cadena literal `r"^\s*(?:#|$)"` debe ser pasado al macro `@r_str` y el resultado de esa expansión debe ser colocado en el árbol de sintaxis donde ocurre la cadena literal. En otras palabras, la expresión `r"^\s*(?:#|$)"` es equivalente a colocar el siguiente objeto directamente en el árbol de sintaxis:

```julia
Regex("^\\s*(?:#|\$)")
```

No solo es más corta y conveniente la forma de literal de cadena, sino que también es más eficiente: dado que la expresión regular se compila y el objeto `Regex` se crea *cuando se compila el código*, la compilación ocurre solo una vez, en lugar de cada vez que se ejecuta el código. Considera si la expresión regular ocurre en un bucle:

```julia
for line = lines
    m = match(r"^\s*(?:#|$)", line)
    if m === nothing
        # non-comment
    else
        # comment
    end
end
```

Dado que la expresión regular `r"^\s*(?:#|$)"` se compila e inserta en el árbol de sintaxis cuando se analiza este código, la expresión solo se compila una vez en lugar de cada vez que se ejecuta el bucle. Para lograr esto sin macros, uno tendría que escribir este bucle de la siguiente manera:

```julia
re = Regex("^\\s*(?:#|\$)")
for line = lines
    m = match(re, line)
    if m === nothing
        # non-comment
    else
        # comment
    end
end
```

Además, si el compilador no puede determinar que el objeto regex es constante en todos los bucles, ciertas optimizaciones podrían no ser posibles, lo que haría que esta versión sea aún menos eficiente que la forma literal más conveniente mencionada anteriormente. Por supuesto, todavía hay situaciones en las que la forma no literal es más conveniente: si se necesita interpolar una variable en la expresión regular, se debe adoptar este enfoque más verboso; en casos donde el patrón de la expresión regular en sí es dinámico, cambiando potencialmente en cada iteración del bucle, se debe construir un nuevo objeto de expresión regular en cada iteración. Sin embargo, en la gran mayoría de los casos de uso, las expresiones regulares no se construyen en función de los datos en tiempo de ejecución. En esta mayoría de casos, la capacidad de escribir expresiones regulares como valores en tiempo de compilación es invaluable.

El mecanismo para literales de cadena definidos por el usuario es profundamente, poderosamente poderoso. No solo los literales no estándar de Julia se implementan utilizando esto, sino que la sintaxis de literales de comando (``` `echo "Hola, $persona"` ```) también se implementa utilizando la siguiente macro que parece inofensiva:

```julia
macro cmd(str)
    :(cmd_gen($(shell_parse(str)[1])))
end
```

Por supuesto, una gran cantidad de complejidad está oculta en las funciones utilizadas en esta definición de macro, pero son solo funciones, escritas completamente en Julia. Puedes leer su código fuente y ver exactamente lo que hacen, y todo lo que hacen es construir objetos de expresión que se insertarán en el árbol de sintaxis de tu programa.

Al igual que los literales de cadena, los literales de comando también pueden ser precedidos por un identificador para formar lo que se llaman literales de comando no estándar. Estos literales de comando se analizan como llamadas a macros con nombres especiales. Por ejemplo, la sintaxis ```custom`literal` ``` se analiza como `@custom_cmd "literal"`. Julia en sí no contiene literales de comando no estándar, pero los paquetes pueden hacer uso de esta sintaxis. Aparte de la sintaxis diferente y el sufijo `_cmd` en lugar del sufijo `_str`, los literales de comando no estándar se comportan exactamente como los literales de cadena no estándar.

En el caso de que dos módulos proporcionen literales de cadena o comando no estándar con el mismo nombre, es posible calificar el literal de cadena o comando con un nombre de módulo. Por ejemplo, si tanto `Foo` como `Bar` proporcionan el literal de cadena no estándar `@x_str`, entonces se puede escribir `Foo.x"literal"` o `Bar.x"literal"` para desambiguar entre los dos.

Otra forma de definir un macro sería así:

```julia
macro foo_str(str, flag)
    # do stuff
end
```

Esta macro se puede llamar con la siguiente sintaxis:

```julia
foo"str"flag
```

El tipo de bandera en la sintaxis mencionada anteriormente sería un `String` con el contenido de lo que sea que siga después del literal de cadena.

## Generated functions

Una macro muy especial es [`@generated`](@ref), que te permite definir lo que se llaman *funciones generadas*. Estas tienen la capacidad de generar código especializado dependiendo de los tipos de sus argumentos con más flexibilidad y/o menos código de lo que se puede lograr con el despacho múltiple. Mientras que las macros trabajan con expresiones en el tiempo de análisis y no pueden acceder a los tipos de sus entradas, una función generada se expande en un momento en que los tipos de los argumentos son conocidos, pero la función aún no está compilada.

En lugar de realizar algún cálculo o acción, una declaración de función generada devuelve una expresión entre comillas que luego forma el cuerpo del método correspondiente a los tipos de los argumentos. Cuando se llama a una función generada, la expresión que devuelve se compila y luego se ejecuta. Para hacer esto eficiente, el resultado generalmente se almacena en caché. Y para hacer esto inferible, solo se puede utilizar un subconjunto limitado del lenguaje. Así, las funciones generadas proporcionan una forma flexible de trasladar trabajo del tiempo de ejecución al tiempo de compilación, a expensas de mayores restricciones sobre los constructos permitidos.

Al definir funciones generadas, hay cinco diferencias principales con respecto a las funciones ordinarias:

1. Anotas la declaración de la función con el macro `@generated`. Esto añade información al AST que permite al compilador saber que esta es una función generada.
2. En el cuerpo de la función generada, solo tienes acceso a los *tipos* de los argumentos, no a sus valores.
3. En lugar de calcular algo o realizar alguna acción, devuelves una *expresión citada* que, cuando se evalúa, hace lo que deseas.
4. Las funciones generadas solo pueden llamar a funciones que fueron definidas *antes* de la definición de la función generada. (No seguir esto puede resultar en obtener `MethodErrors` que se refieren a funciones de una edad de mundo futura.)
5. Las funciones generadas no deben *mutar* ni *observar* ningún estado global no constante (incluyendo, por ejemplo, IO, bloqueos, diccionarios no locales, o usar [`hasmethod`](@ref)). Esto significa que solo pueden leer constantes globales y no pueden tener efectos secundarios. En otras palabras, deben ser completamente puras. Debido a una limitación de implementación, esto también significa que actualmente no pueden definir un cierre o generador.

Es más fácil ilustrar esto con un ejemplo. Podemos declarar una función generada `foo` como

```jldoctest generated
julia> @generated function foo(x)
           Core.println(x)
           return :(x * x)
       end
foo (generic function with 1 method)
```

Tenga en cuenta que el cuerpo devuelve una expresión citada, a saber, `:(x * x)`, en lugar de solo el valor de `x * x`.

Desde la perspectiva del llamador, esto es idéntico a una función regular; de hecho, no tienes que saber si estás llamando a una función regular o generada. Veamos cómo se comporta `foo`:

```jldoctest generated
julia> x = foo(2); # note: output is from println() statement in the body
Int64

julia> x           # now we print x
4

julia> y = foo("bar");
String

julia> y
"barbar"
```

Entonces, vemos que en el cuerpo de la función generada, `x` es el *tipo* del argumento pasado, y el valor devuelto por la función generada es el resultado de evaluar la expresión citada que devolvimos de la definición, ahora con el *valor* de `x`.

¿Qué sucede si evaluamos `foo` nuevamente con un tipo que ya hemos utilizado?

```jldoctest generated
julia> foo(4)
16
```

Tenga en cuenta que no hay una impresión de [`Int64`](@ref). Podemos ver que el cuerpo de la función generada solo se ejecutó una vez aquí, para el conjunto específico de tipos de argumentos, y el resultado fue almacenado en caché. Después de eso, para este ejemplo, la expresión devuelta de la función generada en la primera invocación se reutilizó como el cuerpo del método. Sin embargo, el comportamiento real de almacenamiento en caché es una optimización de rendimiento definida por la implementación, por lo que no es válido depender demasiado de este comportamiento.

El número de veces que se genera una función generada *podría* ser solo una vez, pero *también podría* ser más a menudo, o parecer que no ocurre en absoluto. Como consecuencia, *nunca* debes escribir una función generada con efectos secundarios: cuándo y con qué frecuencia ocurren los efectos secundarios es indefinido. (Esto es cierto también para los macros - y al igual que con los macros, el uso de [`eval`](@ref) en una función generada es una señal de que estás haciendo algo de la manera incorrecta). Sin embargo, a diferencia de los macros, el sistema de tiempo de ejecución no puede manejar correctamente una llamada a `4d61726b646f776e2e436f64652822222c20226576616c2229_40726566`, por lo que está prohibido.

También es importante ver cómo las funciones `@generated` interactúan con la redefinición de métodos. Siguiendo el principio de que una función `@generated` correcta no debe observar ningún estado mutable ni causar ninguna mutación del estado global, vemos el siguiente comportamiento. Observe que la función generada *no puede* llamar a ningún método que no haya sido definido antes de la *definición* de la función generada en sí.

Inicialmente `f(x)` tiene una definición

```jldoctest redefinition
julia> f(x) = "original definition";
```

Define otras operaciones que usen `f(x)`:

```jldoctest redefinition
julia> g(x) = f(x);

julia> @generated gen1(x) = f(x);

julia> @generated gen2(x) = :(f(x));
```

Ahora añadimos algunas nuevas definiciones para `f(x)`:

```jldoctest redefinition
julia> f(x::Int) = "definition for Int";

julia> f(x::Type{Int}) = "definition for Type{Int}";
```

y compara cómo difieren estos resultados:

```jldoctest redefinition
julia> f(1)
"definition for Int"

julia> g(1)
"definition for Int"

julia> gen1(1)
"original definition"

julia> gen2(1)
"definition for Int"
```

Cada método de una función generada tiene su propia visión de las funciones definidas:

```jldoctest redefinition
julia> @generated gen1(x::Real) = f(x);

julia> gen1(1)
"definition for Type{Int}"
```

La función generada de ejemplo `foo` arriba no hizo nada que una función normal `foo(x) = x * x` no pudiera hacer (excepto imprimir el tipo en la primera invocación y generar una sobrecarga mayor). Sin embargo, el poder de una función generada radica en su capacidad para calcular diferentes expresiones citadas dependiendo de los tipos que se le pasen:

```jldoctest
julia> @generated function bar(x)
           if x <: Integer
               return :(x ^ 2)
           else
               return :(x)
           end
       end
bar (generic function with 1 method)

julia> bar(4)
16

julia> bar("baz")
"baz"
```

(aunque, por supuesto, este ejemplo artificial se implementaría más fácilmente utilizando despacho múltiple...)

Abusar de esto corromperá el sistema de ejecución y causará un comportamiento indefinido:

```jldoctest
julia> @generated function baz(x)
           if rand() < .9
               return :(x^2)
           else
               return :("boo!")
           end
       end
baz (generic function with 1 method)
```

Dado que el cuerpo de la función generada es no determinista, su comportamiento, *y el comportamiento de todo el código subsiguiente* es indefinido.

*¡No copies estos ejemplos!*

Estos ejemplos son, con suerte, útiles para ilustrar cómo funcionan las funciones generadas, tanto en el final de la definición como en el sitio de llamada; sin embargo, *no los copies*, por las siguientes razones:

  * la función `foo` tiene efectos secundarios (la llamada a `Core.println`), y es indefinido exactamente cuándo, con qué frecuencia o cuántas veces ocurrirán estos efectos secundarios.
  * la función `bar` resuelve un problema que se resuelve mejor con despacho múltiple - definir `bar(x) = x` y `bar(x::Integer) = x ^ 2` hará lo mismo, pero es tanto más simple como más rápido.
  * la función `baz` es patológica

Tenga en cuenta que el conjunto de operaciones que no deben intentarse en una función generada es ilimitado, y el sistema de tiempo de ejecución actualmente solo puede detectar un subconjunto de las operaciones inválidas. Hay muchas otras operaciones que simplemente corromperán el sistema de tiempo de ejecución sin notificación, generalmente de maneras sutiles que no están obviamente conectadas a la mala definición. Dado que el generador de funciones se ejecuta durante la inferencia, debe respetar todas las limitaciones de ese código.

Algunas operaciones que no deben intentarse incluyen:

1. Caché de punteros nativos.
2. Interactuando con los contenidos o métodos de `Core.Compiler` de cualquier manera.
3. Observando cualquier estado mutable.

      * La inferencia sobre la función generada puede ejecutarse en *cualquier* momento, incluso mientras tu código intenta observar o mutar este estado.
4. Tomando cualquier bloqueo: El código C al que llamas puede usar bloqueos internamente (por ejemplo, no es problemático llamar a `malloc`, aunque la mayoría de las implementaciones requieren bloqueos internamente), pero no intentes mantener o adquirir ninguno mientras ejecutas código Julia.
5. Llamar a cualquier función que esté definida después del cuerpo de la función generada. Esta condición se relaja para los módulos precompilados cargados de forma incremental para permitir llamar a cualquier función en el módulo.

De acuerdo, ahora que tenemos una mejor comprensión de cómo funcionan las funciones generadas, utilicemoslas para construir algunas funcionalidades más avanzadas (y válidas)...

### An advanced example

La biblioteca base de Julia tiene una función interna `sub2ind` para calcular un índice lineal en un arreglo n-dimensional, basado en un conjunto de n índices multilineales; en otras palabras, para calcular el índice `i` que se puede usar para indexar en un arreglo `A` utilizando `A[i]`, en lugar de `A[x,y,z,...]`. Una posible implementación es la siguiente:

```jldoctest sub2ind
julia> function sub2ind_loop(dims::NTuple{N}, I::Integer...) where N
           ind = I[N] - 1
           for i = N-1:-1:1
               ind = I[i]-1 + dims[i]*ind
           end
           return ind + 1
       end;

julia> sub2ind_loop((3, 5), 1, 2)
4
```

Lo mismo se puede hacer utilizando recursión:

```jldoctest
julia> sub2ind_rec(dims::Tuple{}) = 1;

julia> sub2ind_rec(dims::Tuple{}, i1::Integer, I::Integer...) =
           i1 == 1 ? sub2ind_rec(dims, I...) : throw(BoundsError());

julia> sub2ind_rec(dims::Tuple{Integer, Vararg{Integer}}, i1::Integer) = i1;

julia> sub2ind_rec(dims::Tuple{Integer, Vararg{Integer}}, i1::Integer, I::Integer...) =
           i1 + dims[1] * (sub2ind_rec(Base.tail(dims), I...) - 1);

julia> sub2ind_rec((3, 5), 1, 2)
4
```

Ambas estas implementaciones, aunque diferentes, hacen esencialmente lo mismo: un bucle de tiempo de ejecución sobre las dimensiones del arreglo, recopilando el desplazamiento en cada dimensión en el índice final.

Sin embargo, toda la información que necesitamos para el bucle está incrustada en la información de tipo de los argumentos. Esto permite que el compilador mueva la iteración al tiempo de compilación y elimine los bucles en tiempo de ejecución por completo. Podemos utilizar funciones generadas para lograr un efecto similar; en el lenguaje del compilador, usamos funciones generadas para desenrollar manualmente el bucle. El cuerpo se vuelve casi idéntico, pero en lugar de calcular el índice lineal, construimos una *expresión* que calcula el índice:

```jldoctest sub2ind_gen
julia> @generated function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

**¿Qué código generará esto?**

Una forma fácil de averiguarlo es extraer el cuerpo en otra función (regular):

```jldoctest sub2ind_gen2
julia> function sub2ind_gen_impl(dims::Type{T}, I...) where T <: NTuple{N,Any} where N
           length(I) == N || return :(error("partial indexing is unsupported"))
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> @generated function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           return sub2ind_gen_impl(dims, I...)
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

Ahora podemos ejecutar `sub2ind_gen_impl` y examinar la expresión que devuelve:

```jldoctest sub2ind_gen2
julia> sub2ind_gen_impl(Tuple{Int,Int}, Int, Int)
:(((I[1] - 1) + dims[1] * (I[2] - 1)) + 1)
```

Entonces, el cuerpo del método que se utilizará aquí no incluye un bucle en absoluto: solo indexación en las dos tuplas, multiplicación y suma/resta. Todo el bucle se realiza en tiempo de compilación, y evitamos el bucle durante la ejecución por completo. Así, solo hacemos un bucle *una vez por tipo*, en este caso una vez por `N` (excepto en casos límite donde la función se genera más de una vez - ver el descargo de responsabilidad anterior).

### Optionally-generated functions

Las funciones generadas pueden lograr una alta eficiencia en tiempo de ejecución, pero vienen con un costo en tiempo de compilación: se debe generar un nuevo cuerpo de función para cada combinación de tipos de argumentos concretos. Típicamente, Julia puede compilar versiones "genéricas" de funciones que funcionarán para cualquier argumento, pero con funciones generadas esto es imposible. Esto significa que los programas que hacen un uso intensivo de funciones generadas podrían ser imposibles de compilar estáticamente.

Para resolver este problema, el lenguaje proporciona una sintaxis para escribir implementaciones alternativas normales, no generadas, de funciones generadas. Aplicado al ejemplo de `sub2ind` anterior, se vería así:

```jldoctest sub2ind_gen_opt
julia> function sub2ind_gen_impl(dims::Type{T}, I...) where T <: NTuple{N,Any} where N
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> function sub2ind_gen_fallback(dims::NTuple{N}, I) where N
           ind = I[N] - 1
           for i = (N - 1):-1:1
               ind = I[i] - 1 + dims[i]*ind
           end
           return ind + 1
       end;

julia> function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           length(I) == N || error("partial indexing is unsupported")
           if @generated
               return sub2ind_gen_impl(dims, I...)
           else
               return sub2ind_gen_fallback(dims, I)
           end
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

Internamente, este código crea dos implementaciones de la función: una generada donde se utiliza el primer bloque en `if @generated`, y una normal donde se utiliza el bloque `else`. Dentro de la parte `then` del bloque `if @generated`, el código tiene la misma semántica que otras funciones generadas: los nombres de los argumentos se refieren a tipos, y el código debe devolver una expresión. Pueden ocurrir múltiples bloques `if @generated`, en cuyo caso la implementación generada utiliza todos los bloques `then` y la implementación alternativa utiliza todos los bloques `else`.

Tenga en cuenta que hemos agregado una verificación de errores en la parte superior de la función. Este código será común a ambas versiones y se ejecuta en tiempo de ejecución en ambas versiones (se citará y se devolverá como una expresión de la versión generada). Eso significa que los valores y tipos de las variables locales no están disponibles en el momento de la generación de código; el código de generación de código solo puede ver los tipos de los argumentos.

En este estilo de definición, la característica de generación de código es esencialmente una optimización opcional. El compilador la utilizará si es conveniente, pero de lo contrario puede optar por usar la implementación normal. Este estilo es preferido, ya que permite al compilador tomar más decisiones y compilar programas de más maneras, y dado que el código normal es más legible que el código que genera código. Sin embargo, qué implementación se utiliza depende de los detalles de implementación del compilador, por lo que es esencial que las dos implementaciones se comporten de manera idéntica.
