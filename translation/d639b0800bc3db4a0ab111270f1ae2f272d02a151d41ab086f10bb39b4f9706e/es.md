# Control Flow

Julia proporciona una variedad de construcciones de control de flujo:

  * [Compound Expressions](@ref man-compound-expressions): `comenzar` y `;`.
  * [Conditional Evaluation](@ref man-conditional-evaluation): `si`-`si no`-`sino` y `?:` (operador ternario).
  * [Short-Circuit Evaluation](@ref): operadores lógicos `&&` (“y”) y `||` (“o”), y también comparaciones encadenadas.
  * [Repeated Evaluation: Loops](@ref man-loops): `mientras` y `para`.
  * [Exception Handling](@ref): `intentar`-`capturar`, [`error`](@ref) y [`throw`](@ref).
  * [Tasks (aka Coroutines)](@ref man-tasks): [`yieldto`](@ref).

Los primeros cinco mecanismos de control de flujo son estándar en los lenguajes de programación de alto nivel. [`Task`](@ref) no son tan estándar: proporcionan control de flujo no local, lo que hace posible cambiar entre cálculos temporalmente suspendidos. Esta es una construcción poderosa: tanto el manejo de excepciones como el multitasking cooperativo se implementan en Julia utilizando tareas. La programación cotidiana no requiere un uso directo de tareas, pero ciertos problemas se pueden resolver mucho más fácilmente utilizando tareas.

## [Compound Expressions](@id man-compound-expressions)

A veces es conveniente tener una única expresión que evalúe varias subexpresiones en orden, devolviendo el valor de la última subexpresión como su valor. Hay dos construcciones en Julia que logran esto: bloques `begin` y cadenas `;`. El valor de ambas construcciones de expresión compuesta es el de la última subexpresión. Aquí hay un ejemplo de un bloque `begin`:

```jldoctest
julia> z = begin
           x = 1
           y = 2
           x + y
       end
3
```

Dado que estas son expresiones bastante pequeñas y simples, podrían colocarse fácilmente en una sola línea, donde la sintaxis de cadena `;` resulta útil:

```jldoctest
julia> z = (x = 1; y = 2; x + y)
3
```

Esta sintaxis es particularmente útil con la forma de definición de función de una sola línea introducida en [Functions](@ref man-functions). Aunque es típico, no hay un requisito de que los bloques `begin` sean multilínea o que las cadenas `;` sean de una sola línea:

```jldoctest
julia> begin x = 1; y = 2; x + y end
3

julia> (x = 1;
        y = 2;
        x + y)
3
```

## [Conditional Evaluation](@id man-conditional-evaluation)

La evaluación condicional permite que partes del código se evalúen o no se evalúen dependiendo del valor de una expresión booleana. Aquí está la anatomía de la sintaxis condicional `if`-`elseif`-`else`:

```julia
if x < y
    println("x is less than y")
elseif x > y
    println("x is greater than y")
else
    println("x is equal to y")
end
```

Si la expresión de condición `x < y` es `true`, entonces se evalúa el bloque correspondiente; de lo contrario, se evalúa la expresión de condición `x > y`, y si es `true`, se evalúa el bloque correspondiente; si ninguna de las expresiones es verdadera, se evalúa el bloque `else`. Aquí está en acción:

```jldoctest
julia> function test(x, y)
           if x < y
               println("x is less than y")
           elseif x > y
               println("x is greater than y")
           else
               println("x is equal to y")
           end
       end
test (generic function with 1 method)

julia> test(1, 2)
x is less than y

julia> test(2, 1)
x is greater than y

julia> test(1, 1)
x is equal to y
```

Los bloques `elseif` y `else` son opcionales, y se pueden usar tantos bloques `elseif` como se desee. Las expresiones de condición en la construcción `if`-`elseif`-`else` se evalúan hasta que la primera evalúa a `true`, después de lo cual se evalúa el bloque asociado, y no se evalúan más expresiones de condición ni bloques.

Los bloques `if` son "porosos", es decir, no introducen un ámbito local. Esto significa que las nuevas variables definidas dentro de las cláusulas `if` pueden ser utilizadas después del bloque `if`, incluso si no fueron definidas antes. Así que podríamos haber definido la función `test` arriba como

```jldoctest
julia> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           else
               relation = "greater than"
           end
           println("x is ", relation, " y.")
       end
test (generic function with 1 method)

julia> test(2, 1)
x is greater than y.
```

La variable `relation` se declara dentro del bloque `if`, pero se utiliza fuera. Sin embargo, al depender de este comportamiento, asegúrate de que todos los posibles caminos de código definan un valor para la variable. El siguiente cambio en la función anterior resulta en un error en tiempo de ejecución.

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           end
           println("x is ", relation, " y.")
       end
test (generic function with 1 method)

julia> test(1,2)
x is less than y.

julia> test(2,1)
ERROR: UndefVarError: `relation` not defined in local scope
Stacktrace:
 [1] test(::Int64, ::Int64) at ./none:7
```

`if` los bloques también devuelven un valor, lo que puede parecer poco intuitivo para los usuarios que provienen de muchos otros lenguajes. Este valor es simplemente el valor de retorno de la última declaración ejecutada en la rama que fue elegida, así que

```jldoctest
julia> x = 3
3

julia> if x > 0
           "positive!"
       else
           "negative..."
       end
"positive!"
```

Ten en cuenta que las declaraciones condicionales muy cortas (de una línea) se expresan con frecuencia utilizando la Evaluación de Cortocircuito en Julia, como se detalla en la siguiente sección.

A diferencia de C, MATLAB, Perl, Python y Ruby – pero al igual que Java y algunos otros lenguajes más estrictos y tipados – es un error si el valor de una expresión condicional no es `true` o `false`:

```jldoctest
julia> if 1
           println("true")
       end
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

Este error indica que la condición era del tipo incorrecto: [`Int64`](@ref) en lugar del requerido [`Bool`](@ref).

El llamado "operador ternario", `?:`, está estrechamente relacionado con la sintaxis `if`-`elseif`-`else`, pero se utiliza donde se requiere una elección condicional entre valores de expresión únicos, a diferencia de la ejecución condicional de bloques de código más largos. Su nombre proviene de ser el único operador en la mayoría de los lenguajes que toma tres operandos:

```julia
a ? b : c
```

La expresión `a`, antes del `?`, es una expresión de condición, y la operación ternaria evalúa la expresión `b`, antes del `:`, si la condición `a` es `true` o la expresión `c`, después del `:`, si es `false`. Tenga en cuenta que los espacios alrededor de `?` y `:` son obligatorios: una expresión como `a?b:c` no es una expresión ternaria válida (pero se acepta un salto de línea después de ambos, `?` y `:`).

La forma más fácil de entender este comportamiento es ver un ejemplo. En el ejemplo anterior, la llamada a `println` es compartida por las tres ramas: la única elección real es qué cadena literal imprimir. Esto podría escribirse de manera más concisa utilizando el operador ternario. Para mayor claridad, intentemos primero una versión de dos vías:

```jldoctest
julia> x = 1; y = 2;

julia> println(x < y ? "less than" : "not less than")
less than

julia> x = 1; y = 0;

julia> println(x < y ? "less than" : "not less than")
not less than
```

Si la expresión `x < y` es verdadera, toda la expresión del operador ternario se evalúa como la cadena `"less than"` y, de lo contrario, se evalúa como la cadena `"not less than"`. El ejemplo original de tres vías requiere encadenar múltiples usos del operador ternario juntos:

```jldoctest
julia> test(x, y) = println(x < y ? "x is less than y"    :
                            x > y ? "x is greater than y" : "x is equal to y")
test (generic function with 1 method)

julia> test(1, 2)
x is less than y

julia> test(2, 1)
x is greater than y

julia> test(1, 1)
x is equal to y
```

Para facilitar la encadenación, el operador se asocia de derecha a izquierda.

Es significativo que, al igual que `if`-`elseif`-`else`, las expresiones antes y después de los `:` solo se evalúan si la expresión de condición se evalúa como `true` o `false`, respectivamente:

```jldoctest
julia> v(x) = (println(x); x)
v (generic function with 1 method)

julia> 1 < 2 ? v("yes") : v("no")
yes
"yes"

julia> 1 > 2 ? v("yes") : v("no")
no
"no"
```

## Short-Circuit Evaluation

Los operadores `&&` y `||` en Julia corresponden a las operaciones lógicas "y" y "o", respectivamente, y se utilizan típicamente para este propósito. Sin embargo, tienen una propiedad adicional de evaluación *corta*: no necesariamente evalúan su segundo argumento, como se explica a continuación. (También hay operadores a nivel de bits `&` y `|` que se pueden usar como "y" y "o" lógicos *sin* comportamiento de cortocircuito, pero ten en cuenta que `&` y `|` tienen una precedencia más alta que `&&` y `||` para el orden de evaluación.)

La evaluación de cortocircuito es bastante similar a la evaluación condicional. El comportamiento se encuentra en la mayoría de los lenguajes de programación imperativos que tienen los operadores booleanos `&&` y `||`: en una serie de expresiones booleanas conectadas por estos operadores, solo se evalúan el número mínimo de expresiones necesarias para determinar el valor booleano final de toda la cadena. Algunos lenguajes (como Python) se refieren a ellos como `and` (`&&`) y `or` (`||`). Explícitamente, esto significa que:

  * En la expresión `a && b`, la subexpresión `b` solo se evalúa si `a` evalúa a `true`.
  * En la expresión `a || b`, la subexpresión `b` solo se evalúa si `a` evalúa a `false`.

El razonamiento es que `a && b` debe ser `false` si `a` es `false`, independientemente del valor de `b`, y de igual manera, el valor de `a || b` debe ser `true` si `a` es `true`, independientemente del valor de `b`. Tanto `&&` como `||` se asocian a la derecha, pero `&&` tiene una precedencia más alta que `||`. Es fácil experimentar con este comportamiento:

```jldoctest tandf
julia> t(x) = (println(x); true)
t (generic function with 1 method)

julia> f(x) = (println(x); false)
f (generic function with 1 method)

julia> t(1) && t(2)
1
2
true

julia> t(1) && f(2)
1
2
false

julia> f(1) && t(2)
1
false

julia> f(1) && f(2)
1
false

julia> t(1) || t(2)
1
true

julia> t(1) || f(2)
1
true

julia> f(1) || t(2)
1
2
true

julia> f(1) || f(2)
1
2
false
```

Puedes experimentar fácilmente de la misma manera con la asociatividad y precedencia de varias combinaciones de los operadores `&&` y `||`.

Este comportamiento se utiliza frecuentemente en Julia para formar una alternativa a las declaraciones `if` muy cortas. En lugar de `if <cond> <statement> end`, se puede escribir `<cond> && <statement>` (que podría leerse como: <cond> *y luego* <statement>). De manera similar, en lugar de `if ! <cond> <statement> end`, se puede escribir `<cond> || <statement>` (que podría leerse como: <cond> *o de lo contrario* <statement>).

Por ejemplo, una rutina recursiva de factorial podría definirse así:

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function fact(n::Int)
           n >= 0 || error("n must be non-negative")
           n == 0 && return 1
           n * fact(n-1)
       end
fact (generic function with 1 method)

julia> fact(5)
120

julia> fact(0)
1

julia> fact(-1)
ERROR: n must be non-negative
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fact(::Int64) at ./none:2
 [3] top-level scope
```

Las operaciones booleanas *sin* evaluación de cortocircuito se pueden realizar con los operadores booleanos a nivel de bits introducidos en [Mathematical Operations and Elementary Functions](@ref): `&` y `|`. Estas son funciones normales, que casualmente admiten la sintaxis de operador infijo, pero siempre evalúan sus argumentos:

```jldoctest tandf
julia> f(1) & t(2)
1
2
false

julia> t(1) | t(2)
1
2
true
```

Al igual que las expresiones de condición utilizadas en `if`, `elseif` o el operador ternario, los operandos de `&&` o `||` deben ser valores booleanos (`true` o `false`). Usar un valor no booleano en cualquier lugar excepto en la última entrada de una cadena condicional es un error:

```jldoctest
julia> 1 && true
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

Por otro lado, cualquier tipo de expresión se puede utilizar al final de una cadena condicional. Se evaluará y se devolverá dependiendo de las condiciones precedentes:

```jldoctest
julia> true && (x = (1, 2, 3))
(1, 2, 3)

julia> false && (x = (1, 2, 3))
false
```

## [Repeated Evaluation: Loops](@id man-loops)

Hay dos construcciones para la evaluación repetida de expresiones: el bucle `while` y el bucle `for`. Aquí hay un ejemplo de un bucle `while`:

```jldoctest
julia> i = 1;

julia> while i <= 3
           println(i)
           global i += 1
       end
1
2
3
```

El bucle `while` evalúa la expresión de condición (`i <= 3` en este caso), y mientras siga siendo `true`, también sigue evaluando el cuerpo del bucle `while`. Si la expresión de condición es `false` cuando se alcanza por primera vez el bucle `while`, el cuerpo nunca se evalúa.

El bucle `for` facilita la escritura de idioms de evaluación repetida comunes. Dado que contar hacia arriba y hacia abajo, como lo hace el bucle `while` anterior, es tan común, se puede expresar de manera más concisa con un bucle `for`:

```jldoctest
julia> for i = 1:3
           println(i)
       end
1
2
3
```

Aquí el `1:3` es un objeto [`range`](@ref), que representa la secuencia de números 1, 2, 3. El bucle `for` itera a través de estos valores, asignando cada uno a su vez a la variable `i`. En general, el constructo `for` puede iterar sobre cualquier objeto "iterable" (o "contenedor"), desde un rango como `1:3` o `1:3:13` (un [`StepRange`](@ref) que indica cada tercer entero 1, 4, 7, …, 13) hasta contenedores más genéricos como arreglos, incluyendo [iterators defined by user code](@ref man-interface-iteration) o paquetes externos. Para contenedores que no son rangos, la palabra clave alternativa (pero totalmente equivalente) `in` o `∈` se utiliza típicamente en lugar de `=`, ya que hace que el código sea más claro:

```jldoctest
julia> for i in [1,4,0]
           println(i)
       end
1
4
0

julia> for s ∈ ["foo","bar","baz"]
           println(s)
       end
foo
bar
baz
```

Se introducirán y discutirán varios tipos de contenedores iterables en secciones posteriores del manual (ver, por ejemplo, [Multi-dimensional Arrays](@ref man-multi-dim-arrays)).

Una distinción bastante importante entre la forma del bucle `while` anterior y la forma del bucle `for` es el alcance durante el cual la variable es visible. Un bucle `for` siempre introduce una nueva variable de iteración en su cuerpo, independientemente de si existe una variable con el mismo nombre en el ámbito que lo rodea. Esto implica que, por un lado, `i` no necesita ser declarada antes del bucle. Por otro lado, no será visible fuera del bucle, ni se verá afectada una variable externa con el mismo nombre. Necesitarás una nueva instancia de sesión interactiva o un nombre de variable diferente para probar esto:

```jldoctest
julia> for j = 1:3
           println(j)
       end
1
2
3

julia> j
ERROR: UndefVarError: `j` not defined in `Main`
```

```jldoctest
julia> j = 0;

julia> for j = 1:3
           println(j)
       end
1
2
3

julia> j
0
```

Utiliza `for outer` para modificar el comportamiento posterior y reutilizar una variable local existente.

Consulta [Scope of Variables](@ref scope-of-variables) para una explicación detallada del alcance de las variables, [`outer`](@ref), y cómo funciona en Julia.

A veces es conveniente terminar la repetición de un `while` antes de que la condición de prueba sea falsificada o detener la iteración en un bucle `for` antes de que se alcance el final del objeto iterable. Esto se puede lograr con la palabra clave `break`:

```jldoctest
julia> i = 1;

julia> while true
           println(i)
           if i >= 3
               break
           end
           global i += 1
       end
1
2
3

julia> for j = 1:1000
           println(j)
           if j >= 3
               break
           end
       end
1
2
3
```

Sin la palabra clave `break`, el bucle `while` anterior nunca se terminaría por sí solo, y el bucle `for` iteraría hasta 1000. Ambos bucles se salen anticipadamente utilizando `break`.

En otras circunstancias, es útil poder detener una iteración y pasar a la siguiente de inmediato. La palabra clave `continue` logra esto:

```jldoctest
julia> for i = 1:10
           if i % 3 != 0
               continue
           end
           println(i)
       end
3
6
9
```

Este es un ejemplo algo forzado, ya que podríamos producir el mismo comportamiento de manera más clara negando la condición y colocando la llamada a `println` dentro del bloque `if`. En un uso realista, hay más código que se evalúa después del `continue`, y a menudo hay múltiples puntos desde los cuales se llama a `continue`.

Múltiples bucles `for` anidados se pueden combinar en un solo bucle externo, formando el producto cartesiano de sus iterables:

```jldoctest
julia> for i = 1:2, j = 3:4
           println((i, j))
       end
(1, 3)
(1, 4)
(2, 3)
(2, 4)
```

Con esta sintaxis, los iterables aún pueden referirse a las variables del bucle exterior; por ejemplo, `for i = 1:n, j = 1:i` es válido. Sin embargo, una declaración `break` dentro de dicho bucle sale de todo el anidamiento de bucles, no solo del interior. Ambas variables (`i` y `j`) se establecen en sus valores de iteración actuales cada vez que se ejecuta el bucle interno. Por lo tanto, las asignaciones a `i` no serán visibles para las iteraciones subsiguientes:

```jldoctest
julia> for i = 1:2, j = 3:4
           println((i, j))
           i = 0
       end
(1, 3)
(1, 4)
(2, 3)
(2, 4)
```

Si este ejemplo se reescribiera para usar una palabra clave `for` para cada variable, entonces la salida sería diferente: los segundos y cuartos valores contendrían `0`.

Múltiples contenedores se pueden iterar al mismo tiempo en un solo bucle `for` usando [`zip`](@ref):

```jldoctest
julia> for (j, k) in zip([1 2 3], [4 5 6 7])
           println((j,k))
       end
(1, 4)
(2, 5)
(3, 6)
```

Usando [`zip`](@ref) se creará un iterador que es una tupla que contiene los subiteradores para los contenedores que se le pasen. El iterador `zip` iterará sobre todos los subiteradores en orden, eligiendo el $i$-ésimo elemento de cada subiterador en la $i$-ésima iteración del bucle `for`. Una vez que cualquiera de los subiteradores se agote, el bucle `for` se detendrá.

## Exception Handling

Cuando ocurre una condición inesperada, una función puede no ser capaz de devolver un valor razonable a su llamador. En tales casos, puede ser mejor que la condición excepcional termine el programa mientras imprime un mensaje de error de diagnóstico, o si el programador ha proporcionado código para manejar tales circunstancias excepcionales, entonces permitir que ese código tome la acción apropiada.

### Built-in `Exception`s

Las `Exception`s se lanzan cuando ha ocurrido una condición inesperada. Las `Exception`s integradas que se enumeran a continuación interrumpen el flujo normal de control.

| `Exception`                   |
|:----------------------------- |
| [`ArgumentError`](@ref)       |
| [`BoundsError`](@ref)         |
| [`CompositeException`](@ref)  |
| [`DimensionMismatch`](@ref)   |
| [`DivideError`](@ref)         |
| [`DomainError`](@ref)         |
| [`EOFError`](@ref)            |
| [`ErrorException`](@ref)      |
| [`InexactError`](@ref)        |
| [`InitError`](@ref)           |
| [`InterruptException`](@ref)  |
| `InvalidStateException`       |
| [`KeyError`](@ref)            |
| [`LoadError`](@ref)           |
| [`OutOfMemoryError`](@ref)    |
| [`ReadOnlyMemoryError`](@ref) |
| [`RemoteException`](@ref)     |
| [`MethodError`](@ref)         |
| [`OverflowError`](@ref)       |
| [`Meta.ParseError`](@ref)     |
| [`SystemError`](@ref)         |
| [`TypeError`](@ref)           |
| [`UndefRefError`](@ref)       |
| [`UndefVarError`](@ref)       |
| [`StringIndexError`](@ref)    |

Por ejemplo, la función [`sqrt`](@ref) lanza un [`DomainError`](@ref) si se aplica a un valor real negativo:

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

Puedes definir tus propias excepciones de la siguiente manera:

```jldoctest
julia> struct MyCustomException <: Exception end
```

### The [`throw`](@ref) function

Las excepciones se pueden crear explícitamente con [`throw`](@ref). Por ejemplo, una función definida solo para números no negativos podría escribirse para `4d61726b646f776e2e436f64652822222c20227468726f772229_40726566` una [`DomainError`](@ref) si el argumento es negativo:

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> f(x) = x>=0 ? exp(-x) : throw(DomainError(x, "argument must be non-negative"))
f (generic function with 1 method)

julia> f(1)
0.36787944117144233

julia> f(-1)
ERROR: DomainError with -1:
argument must be non-negative
Stacktrace:
 [1] f(::Int64) at ./none:1
```

Tenga en cuenta que [`DomainError`](@ref) sin paréntesis no es una excepción, sino un tipo de excepción. Necesita ser llamado para obtener un objeto `Exception`:

```jldoctest
julia> typeof(DomainError(nothing)) <: Exception
true

julia> typeof(DomainError) <: Exception
false
```

Además, algunos tipos de excepciones aceptan uno o más argumentos que se utilizan para la información de errores:

```jldoctest
julia> throw(UndefVarError(:x))
ERROR: UndefVarError: `x` not defined
```

Este mecanismo se puede implementar fácilmente mediante tipos de excepciones personalizadas siguiendo la forma en que se escribe [`UndefVarError`](@ref):

```jldoctest
julia> struct MyUndefVarError <: Exception
           var::Symbol
       end

julia> Base.showerror(io::IO, e::MyUndefVarError) = print(io, e.var, " not defined")
```

!!! note
    Al escribir un mensaje de error, se prefiere que la primera palabra esté en minúscula. Por ejemplo,

    `size(A) == size(B) || throw(DimensionMismatch("el tamaño de A no es igual al tamaño de B"))`

    es preferido sobre

    `size(A) == size(B) || throw(DimensionMismatch("El tamaño de A no es igual al tamaño de B"))`.

    Sin embargo, a veces tiene sentido mantener la primera letra en mayúscula, por ejemplo, si un argumento de una función es una letra mayúscula:

    `size(A,1) == size(B,2) || throw(DimensionMismatch("A tiene la primera dimensión..."))`.


### Errors

La función [`error`](@ref) se utiliza para producir un [`ErrorException`](@ref) que interrumpe el flujo normal de control.

Supongamos que queremos detener la ejecución inmediatamente si se toma la raíz cuadrada de un número negativo. Para hacer esto, podemos definir una versión difusa de la función [`sqrt`](@ref) que genera un error si su argumento es negativo:

```jldoctest fussy_sqrt; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> fussy_sqrt(x) = x >= 0 ? sqrt(x) : error("negative x not allowed")
fussy_sqrt (generic function with 1 method)

julia> fussy_sqrt(2)
1.4142135623730951

julia> fussy_sqrt(-1)
ERROR: negative x not allowed
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fussy_sqrt(::Int64) at ./none:1
 [3] top-level scope
```

Si `fussy_sqrt` es llamado con un valor negativo desde otra función, en lugar de intentar continuar la ejecución de la función que lo llama, retorna inmediatamente, mostrando el mensaje de error en la sesión interactiva:

```jldoctest fussy_sqrt; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function verbose_fussy_sqrt(x)
           println("before fussy_sqrt")
           r = fussy_sqrt(x)
           println("after fussy_sqrt")
           return r
       end
verbose_fussy_sqrt (generic function with 1 method)

julia> verbose_fussy_sqrt(2)
before fussy_sqrt
after fussy_sqrt
1.4142135623730951

julia> verbose_fussy_sqrt(-1)
before fussy_sqrt
ERROR: negative x not allowed
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fussy_sqrt at ./none:1 [inlined]
 [3] verbose_fussy_sqrt(::Int64) at ./none:3
 [4] top-level scope
```

### The `try/catch` statement

La declaración `try/catch` permite probar `Exception`s y manejar de manera elegante cosas que podrían romper su aplicación. Por ejemplo, en el código a continuación, la función para la raíz cuadrada normalmente lanzaría una excepción. Al colocar un bloque `try/catch` a su alrededor, podemos mitigar eso aquí. Puede elegir cómo desea manejar esta excepción, ya sea registrándola, devolviendo un valor de marcador de posición o, como en el caso a continuación, donde simplemente imprimimos una declaración. Una cosa en la que pensar al decidir cómo manejar situaciones inesperadas es que usar un bloque `try/catch` es mucho más lento que usar ramificación condicional para manejar esas situaciones. A continuación, hay más ejemplos de manejo de excepciones con un bloque `try/catch`:

```jldoctest
julia> try
           sqrt("ten")
       catch e
           println("You should have entered a numeric value")
       end
You should have entered a numeric value
```

Las declaraciones `try/catch` también permiten que la `Excepción` se guarde en una variable. El siguiente ejemplo artificial calcula la raíz cuadrada del segundo elemento de `x` si `x` es indexable, de lo contrario asume que `x` es un número real y devuelve su raíz cuadrada:

```jldoctest
julia> sqrt_second(x) = try
           sqrt(x[2])
       catch y
           if isa(y, DomainError)
               sqrt(complex(x[2], 0))
           elseif isa(y, BoundsError)
               sqrt(x)
           end
       end
sqrt_second (generic function with 1 method)

julia> sqrt_second([1 4])
2.0

julia> sqrt_second([1 -4])
0.0 + 2.0im

julia> sqrt_second(9)
3.0

julia> sqrt_second(-9)
ERROR: DomainError with -9.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

Tenga en cuenta que el símbolo que sigue a `catch` siempre se interpretará como un nombre para la excepción, por lo que se necesita tener cuidado al escribir expresiones `try/catch` en una sola línea. El siguiente código *no* funcionará para devolver el valor de `x` en caso de un error:

```julia
try bad() catch x end
```

En su lugar, utiliza un punto y coma o inserta un salto de línea después de `catch`:

```julia
try bad() catch; x end

try bad()
catch
    x
end
```

El poder de la construcción `try/catch` radica en la capacidad de deshacer una computación profundamente anidada inmediatamente a un nivel mucho más alto en la pila de funciones llamadas. Hay situaciones en las que no ha ocurrido ningún error, pero la capacidad de deshacer la pila y pasar un valor a un nivel superior es deseable. Julia proporciona las funciones [`rethrow`](@ref), [`backtrace`](@ref), [`catch_backtrace`](@ref) y [`current_exceptions`](@ref) para un manejo de errores más avanzado.

### `else` Clauses

!!! compat "Julia 1.8"
    Esta funcionalidad requiere al menos Julia 1.8.


En algunos casos, uno puede no solo querer manejar adecuadamente el caso de error, sino también querer ejecutar algún código solo si el bloque `try` tiene éxito. Para esto, se puede especificar una cláusula `else` después del bloque `catch` que se ejecuta siempre que no se haya lanzado ningún error previamente. La ventaja de incluir este código en el bloque `try` en su lugar es que cualquier error adicional no se captura silenciosamente por la cláusula `catch`.

```julia
local x
try
    x = read("file", String)
catch
    # handle read errors
else
    # do something with x
end
```

!!! note
    Las cláusulas `try`, `catch`, `else` y `finally` introducen cada una sus propios bloques de alcance, por lo que si una variable se define solo en el bloque `try`, no se puede acceder a ella desde la cláusula `else` o `finally`:

    ```jldoctest
    julia> try
               foo = 1
           catch
           else
               foo
           end
    ERROR: UndefVarError: `foo` not defined in `Main`
    Suggestion: check for spelling errors or missing imports.
    ```

    Utiliza el [`local` keyword](@ref local-scope) fuera del bloque `try` para hacer que la variable sea accesible desde cualquier lugar dentro del ámbito exterior.


### `finally` Clauses

En el código que realiza cambios de estado o utiliza recursos como archivos, generalmente hay trabajo de limpieza (como cerrar archivos) que debe hacerse cuando el código ha terminado. Las excepciones pueden complicar esta tarea, ya que pueden hacer que un bloque de código salga antes de alcanzar su final normal. La palabra clave `finally` proporciona una forma de ejecutar algún código cuando un bloque de código dado sale, independientemente de cómo salga.

Por ejemplo, así es como podemos garantizar que un archivo abierto se cierre:

```julia
f = open("file")
try
    # operate on file f
finally
    close(f)
end
```

Cuando el control sale del bloque `try` (por ejemplo, debido a un `return`, o simplemente finalizando normalmente), se ejecutará `close(f)`. Si el bloque `try` sale debido a una excepción, la excepción continuará propagándose. Un bloque `catch` puede combinarse con `try` y `finally` también. En este caso, el bloque `finally` se ejecutará después de que `catch` haya manejado el error.

## [Tasks (aka Coroutines)](@id man-tasks)

Las tareas son una característica de control de flujo que permite que los cálculos se suspendan y reanuden de manera flexible. Las mencionamos aquí solo por completitud; para una discusión completa, consulte [Asynchronous Programming](@ref man-asynchronous).
