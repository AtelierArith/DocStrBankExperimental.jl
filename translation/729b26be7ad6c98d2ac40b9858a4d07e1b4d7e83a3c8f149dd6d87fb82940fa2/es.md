# [Scope of Variables](@id scope-of-variables)

El *alcance* de una variable es la región del código dentro de la cual una variable es accesible. El alcance de las variables ayuda a evitar conflictos en los nombres de las variables. El concepto es intuitivo: dos funciones pueden tener argumentos llamados `x` sin que los dos `x` se refieran a lo mismo. De manera similar, hay muchos otros casos en los que diferentes bloques de código pueden usar el mismo nombre sin referirse a lo mismo. Las reglas sobre cuándo el mismo nombre de variable se refiere o no a lo mismo se llaman reglas de alcance; esta sección las detalla en profundidad.

Ciertos constructos en el lenguaje introducen *bloques de alcance*, que son regiones de código que son elegibles para ser el alcance de un conjunto de variables. El alcance de una variable no puede ser un conjunto arbitrario de líneas de código; en su lugar, siempre se alineará con uno de estos bloques. Hay dos tipos principales de alcances en Julia, *alcance global* y *alcance local*. Este último puede estar anidado. También hay una distinción en Julia entre constructos que introducen un "alcance duro" y aquellos que solo introducen un "alcance blando", lo que afecta si [shadowing](https://en.wikipedia.org/wiki/Variable_shadowing) se permite como una variable global con el mismo nombre o no.

### [Scope constructs](@id man-scope-table)

Los constructos que introducen bloques de alcance son:

| Construct                                                                        | Scope type   | Allowed within |
|:-------------------------------------------------------------------------------- |:------------ |:-------------- |
| [`module`](@ref), [`baremodule`](@ref)                                           | global       | global         |
| [`struct`](@ref)                                                                 | local (soft) | global         |
| [`for`](@ref), [`while`](@ref), [`try`](@ref try)                                | local (soft) | global, local  |
| [`macro`](@ref)                                                                  | local (hard) | global         |
| functions, [`do`](@ref) blocks, [`let`](@ref) blocks, comprehensions, generators | local (hard) | global, local  |

Notablemente ausentes de esta tabla están [begin blocks](@ref man-compound-expressions) y [if blocks](@ref man-conditional-evaluation) que *no* introducen nuevos ámbitos. Los tres tipos de ámbitos siguen reglas algo diferentes que se explicarán a continuación.

Julia usa [lexical scoping](https://en.wikipedia.org/wiki/Scope_(computer_science)#Lexical_scope_vs._dynamic_scope), lo que significa que el alcance de una función no hereda del alcance de su llamador, sino del alcance en el que se definió la función. Por ejemplo, en el siguiente código, el `x` dentro de `foo` se refiere al `x` en el alcance global de su módulo `Bar`:

```jldoctest moduleBar
julia> module Bar
           x = 1
           foo() = x
       end;
```

y no hay un `x` en el ámbito donde se usa `foo`:

```jldoctest moduleBar
julia> import .Bar

julia> x = -1;

julia> Bar.foo()
1
```

Así, *el alcance léxico* significa que a qué se refiere una variable en un fragmento particular de código se puede deducir del código en el que aparece solo y no depende de cómo se ejecute el programa. Un alcance anidado dentro de otro alcance puede "ver" variables en todos los alcances exteriores en los que está contenido. Los alcances exteriores, por otro lado, no pueden ver variables en los alcances internos.

## Global Scope

Cada módulo introduce un nuevo ámbito global, separado del ámbito global de todos los demás módulos; no hay un ámbito global abarcador. Los módulos pueden introducir variables de otros módulos en su ámbito a través de las declaraciones [using or import](@ref modules) o mediante acceso calificado utilizando la notación de punto, es decir, cada módulo es una llamada *espacio de nombres* así como una estructura de datos de primera clase que asocia nombres con valores.

Si una expresión de nivel superior contiene una declaración de variable con la palabra clave `local`, entonces esa variable no es accesible fuera de esa expresión. La variable dentro de la expresión no afecta a las variables globales del mismo nombre. Un ejemplo es declarar `local x` en un bloque `begin` o `if` en el nivel superior:

```jldoctest
julia> x = 1
       begin
           local x = 0
           @show x
       end
       @show x;
x = 0
x = 1
```

Tenga en cuenta que el aviso interactivo (también conocido como REPL) está en el ámbito global del módulo `Main`.

## [Local Scope](@id local-scope)

Un nuevo ámbito local es introducido por la mayoría de los bloques de código (ver arriba [table](@ref man-scope-table) para una lista completa). Si tal bloque está sintácticamente anidado dentro de otro ámbito local, el ámbito que crea está anidado dentro de todos los ámbitos locales en los que aparece, los cuales están, en última instancia, anidados dentro del ámbito global del módulo en el que se evalúa el código. Las variables en los ámbitos exteriores son visibles desde cualquier ámbito que contengan, lo que significa que pueden ser leídas y escritas en los ámbitos internos, a menos que haya una variable local con el mismo nombre que "sombreé" la variable exterior del mismo nombre. Esto es cierto incluso si el ámbito local exterior se declara después (en el sentido de estar textualmente debajo) de un bloque interno. Cuando decimos que una variable "existe" en un ámbito dado, esto significa que una variable con ese nombre existe en cualquiera de los ámbitos que el ámbito actual está anidado, incluido el actual.

Algunos lenguajes de programación requieren declarar explícitamente nuevas variables antes de usarlas. La declaración explícita también funciona en Julia: en cualquier ámbito local, escribir `local x` declara una nueva variable local en ese ámbito, independientemente de si ya hay una variable llamada `x` en un ámbito externo o no. Sin embargo, declarar cada nueva variable de esta manera es algo verboso y tedioso, por lo que Julia, al igual que muchos otros lenguajes, considera que la asignación a un nombre de variable que no existe ya declara implícitamente esa variable. Si el ámbito actual es global, la nueva variable es global; si el ámbito actual es local, la nueva variable es local al ámbito local más interno y será visible dentro de ese ámbito pero no fuera de él. Si asignas a un local existente, *siempre* actualiza ese local existente: solo puedes ocultar un local declarando explícitamente un nuevo local en un ámbito anidado con la palabra clave `local`. En particular, esto se aplica a las variables asignadas en funciones internas, lo que puede sorprender a los usuarios que vienen de Python, donde la asignación en una función interna crea un nuevo local a menos que la variable se declare explícitamente como no local.

Principalmente, esto es bastante intuitivo, pero como con muchas cosas que se comportan de manera intuitiva, los detalles son más sutiles de lo que uno podría imaginar ingenuamente.

Cuando `x = <valor>` ocurre en un ámbito local, Julia aplica las siguientes reglas para decidir qué significa la expresión según dónde ocurre la expresión de asignación y a qué se refiere ya `x` en esa ubicación:

1. **Variable local existente:** Si `x` es *ya una variable local*, entonces se asigna la variable local existente `x`;
2. **Ámbito estricto:** Si `x` *no es ya una variable local* y se produce una asignación dentro de cualquier constructo de ámbito estricto (es decir, dentro de un bloque `let`, el cuerpo de una función o macro, comprensión o generador), se crea una nueva variable local llamada `x` en el ámbito de la asignación;
3. **Alcance suave:** Si `x` *no es ya una variable local* y todos los constructos de alcance que contienen la asignación son alcances suaves (bucles, bloques `try`/`catch`, o bloques `struct`), el comportamiento depende de si la variable global `x` está definida:

      * si `x` global es *indefinido*, se crea un nuevo local llamado `x` en el ámbito de la asignación;
      * si `x` global está *definido*, la asignación se considera ambigua:

          * en contextos *no interactivos* (archivos, eval), se imprime una advertencia de ambigüedad y se crea un nuevo local;
          * en *contextos* interactivos (REPL, notebooks), se asigna la variable global `x`.

Puede notar que en contextos no interactivos, los comportamientos de alcance duro y suave son idénticos, excepto que se imprime una advertencia cuando una variable local implícita (es decir, no declarada con `local x`) oculta una global. En contextos interactivos, las reglas siguen una heurística más compleja por conveniencia. Esto se cubre en profundidad en los ejemplos que siguen.

Ahora que conoces las reglas, veamos algunos ejemplos. Cada ejemplo se asume que se evalúa en una nueva sesión de REPL, de modo que los únicos globales en cada fragmento son los que se asignan en ese bloque de código.

Comenzaremos con una situación clara y sencilla: una asignación dentro de un ámbito restringido, en este caso el cuerpo de una función, cuando no existe ya una variable local con ese nombre:

```jldoctest
julia> function greet()
           x = "hello" # new local
           println(x)
       end
greet (generic function with 1 method)

julia> greet()
hello

julia> x # global
ERROR: UndefVarError: `x` not defined in `Main`
```

Dentro de la función `greet`, la asignación `x = "hello"` hace que `x` sea una nueva variable local en el ámbito de la función. Hay dos hechos relevantes: la asignación ocurre en el ámbito local y no hay ninguna variable local `x` existente. Dado que `x` es local, no importa si hay un `x` global o no. Aquí, por ejemplo, definimos `x = 123` antes de definir y llamar a `greet`:

```jldoctest
julia> x = 123 # global
123

julia> function greet()
           x = "hello" # new local
           println(x)
       end
greet (generic function with 1 method)

julia> greet()
hello

julia> x # global
123
```

Dado que el `x` en `greet` es local, el valor (o la falta de este) del global `x` no se ve afectado al llamar a `greet`. La regla de alcance estricto no se preocupa por si existe o no un global llamado `x`: la asignación a `x` en un alcance estricto es local (a menos que `x` se declare global).

La siguiente situación clara que consideraremos es cuando ya hay una variable local llamada `x`, en cuyo caso `x = <valor>` siempre asigna a este `x` local existente. Esto es cierto ya sea que la asignación ocurra en el mismo ámbito local, en un ámbito local interno en el mismo cuerpo de función, o en el cuerpo de una función anidada dentro de otra función, también conocida como [closure](https://en.wikipedia.org/wiki/Closure_(computer_programming)).

Usaremos la función `sum_to`, que calcula la suma de enteros desde uno hasta `n`, como un ejemplo:

```julia
function sum_to(n)
    s = 0 # new local
    for i = 1:n
        s = s + i # assign existing local
    end
    return s # same local
end
```

Como en el ejemplo anterior, la primera asignación a `s` en la parte superior de `sum_to` hace que `s` sea una nueva variable local en el cuerpo de la función. El bucle `for` tiene su propio ámbito local interno dentro del ámbito de la función. En el punto donde ocurre `s = s + i`, `s` ya es una variable local, por lo que la asignación actualiza el `s` existente en lugar de crear uno nuevo. Podemos probar esto llamando a `sum_to` en el REPL:

```jldoctest
julia> function sum_to(n)
           s = 0 # new local
           for i = 1:n
               s = s + i # assign existing local
           end
           return s # same local
       end
sum_to (generic function with 1 method)

julia> sum_to(10)
55

julia> s # global
ERROR: UndefVarError: `s` not defined in `Main`
```

Dado que `s` es local a la función `sum_to`, llamar a la función no tiene efecto en la variable global `s`. También podemos ver que la actualización `s = s + i` en el bucle `for` debe haber actualizado el mismo `s` creado por la inicialización `s = 0`, ya que obtenemos la suma correcta de 55 para los enteros del 1 al 10.

Vamos a profundizar en el hecho de que el cuerpo del bucle `for` tiene su propio alcance por un segundo, escribiendo una variación ligeramente más verbosa que llamaremos `sum_to_def`, en la que guardamos la suma `s + i` en una variable `t` antes de actualizar `s`:

```jldoctest
julia> function sum_to_def(n)
           s = 0 # new local
           for i = 1:n
               t = s + i # new local `t`
               s = t # assign existing local `s`
           end
           return s, @isdefined(t)
       end
sum_to_def (generic function with 1 method)

julia> sum_to_def(10)
(55, false)
```

Esta versión devuelve `s` como antes, pero también utiliza el macro `@isdefined` para devolver un booleano que indica si hay una variable local llamada `t` definida en el ámbito local más externo de la función. Como puedes ver, no hay un `t` definido fuera del cuerpo del bucle `for`. Esto se debe a la regla de ámbito estricto nuevamente: dado que la asignación a `t` ocurre dentro de una función, que introduce un ámbito estricto, la asignación hace que `t` se convierta en una nueva variable local en el ámbito local donde aparece, es decir, dentro del cuerpo del bucle. Incluso si hubiera un global llamado `t`, no haría ninguna diferencia: la regla de ámbito estricto no se ve afectada por nada en el ámbito global.

Tenga en cuenta que el alcance local de un cuerpo de bucle for no es diferente del alcance local de una función interna. Esto significa que podríamos reescribir este ejemplo de manera que el cuerpo del bucle se implemente como una llamada a una función auxiliar interna y se comporte de la misma manera:

```jldoctest
julia> function sum_to_def_closure(n)
           function loop_body(i)
               t = s + i # new local `t`
               s = t # assign same local `s` as below
           end
           s = 0 # new local
           for i = 1:n
               loop_body(i)
           end
           return s, @isdefined(t)
       end
sum_to_def_closure (generic function with 1 method)

julia> sum_to_def_closure(10)
(55, false)
```

Este ejemplo ilustra un par de puntos clave:

1. Los ámbitos de las funciones internas son como cualquier otro ámbito local anidado. En particular, si una variable ya es local fuera de una función interna y le asignas un valor en la función interna, la variable local externa se actualiza.
2. No importa si la definición de un local externo ocurre por debajo de donde se actualiza, la regla sigue siendo la misma. Todo el ámbito local que lo rodea se analiza y sus locales se determinan antes de que se resuelvan los significados de los locales internos.

Este diseño significa que generalmente puedes mover código dentro o fuera de una función interna sin cambiar su significado, lo que facilita una serie de modismos comunes en el lenguaje que utilizan cierres (ver [do blocks](@ref Do-Block-Syntax-for-Function-Arguments)).

Pasemos a algunos casos más ambiguos cubiertos por la regla de alcance suave. Exploraremos esto extrayendo los cuerpos de las funciones `greet` y `sum_to_def` en contextos de alcance suave. Primero, coloquemos el cuerpo de `greet` en un bucle `for`—que es suave, en lugar de duro—y evaluémoslo en el REPL:

```jldoctest
julia> for i = 1:3
           x = "hello" # new local
           println(x)
       end
hello
hello
hello

julia> x
ERROR: UndefVarError: `x` not defined in `Main`
```

Dado que el `x` global no está definido cuando se evalúa el bucle `for`, se aplica la primera cláusula de la regla de ámbito suave y `x` se crea como local al bucle `for`, por lo tanto, el `x` global permanece indefinido después de que se ejecuta el bucle. A continuación, consideremos el cuerpo de `sum_to_def` extraído al ámbito global, fijando su argumento a `n = 10`.

```julia
s = 0
for i = 1:10
    t = s + i
    s = t
end
s
@isdefined(t)
```

¿Qué hace este código? Pista: es una pregunta engañosa. La respuesta es "depende". Si este código se ingresa de forma interactiva, se comporta de la misma manera que lo hace en el cuerpo de una función. Pero si el código aparece en un archivo, imprime una advertencia de ambigüedad y lanza un error de variable indefinida. Veamos cómo funciona primero en el REPL:

```jldoctest
julia> s = 0 # global
0

julia> for i = 1:10
           t = s + i # new local `t`
           s = t # assign global `s`
       end

julia> s # global
55

julia> @isdefined(t) # global
false
```

El REPL aproxima estar en el cuerpo de una función al decidir si la asignación dentro del bucle asigna a una variable global o crea una nueva local, según si una variable global con ese nombre está definida o no. Si existe una global con ese nombre, entonces la asignación la actualiza. Si no existe ninguna global, entonces la asignación crea una nueva variable local. En este ejemplo vemos ambos casos en acción:

  * No hay ninguna variable global llamada `t`, por lo que `t = s + i` crea un nuevo `t` que es local al bucle `for`;
  * Hay una variable global llamada `s`, así que `s = t` le asigna un valor.

El segundo hecho es por qué la ejecución del bucle cambia el valor global de `s` y el primer hecho es por qué `t` sigue sin estar definido después de que se ejecuta el bucle. Ahora, intentemos evaluar este mismo código como si estuviera en un archivo en su lugar:

```jldoctest
julia> code = """
       s = 0 # global
       for i = 1:10
           t = s + i # new local `t`
           s = t # new local `s` with warning
       end
       s, # global
       @isdefined(t) # global
       """;

julia> include_string(Main, code)
┌ Warning: Assignment to `s` in soft scope is ambiguous because a global variable by the same name exists: `s` will be treated as a new local. Disambiguate by using `local s` to suppress this warning or `global s` to assign to the existing global variable.
└ @ string:4
ERROR: LoadError: UndefVarError: `s` not defined in local scope
```

Aquí usamos [`include_string`](@ref), para evaluar `code` como si fuera el contenido de un archivo. También podríamos guardar `code` en un archivo y luego llamar a `include` en ese archivo; el resultado sería el mismo. Como puedes ver, esto se comporta de manera bastante diferente a evaluar el mismo código en el REPL. Desglosemos lo que está sucediendo aquí:

  * global `s` está definido con el valor `0` antes de que se evalúe el bucle.
  * la asignación `s = t` ocurre en un ámbito suave—un bucle `for` fuera de cualquier cuerpo de función u otra construcción de ámbito duro
  * por lo tanto, se aplica la segunda cláusula de la regla de alcance suave, y la asignación es ambigua, por lo que se emite una advertencia.
  * la ejecución continúa, haciendo que `s` sea local al cuerpo del bucle `for`
  * dado que `s` es local al bucle `for`, está indefinido cuando se evalúa `t = s + i`, lo que causa un error
  * la evaluación se detiene allí, pero si llegara a `s` y `@isdefined(t)`, devolvería `0` y `false`.

Esto demuestra algunos aspectos importantes del alcance: en un alcance, cada variable puede tener solo un significado, y ese significado se determina independientemente del orden de las expresiones. La presencia de la expresión `s = t` en el bucle hace que `s` sea local al bucle, lo que significa que también es local cuando aparece en el lado derecho de `t = s + i`, a pesar de que esa expresión aparece primero y se evalúa primero. Uno podría imaginar que el `s` en la primera línea del bucle podría ser global mientras que el `s` en la segunda línea del bucle es local, pero eso no es posible ya que las dos líneas están en el mismo bloque de alcance y cada variable solo puede significar una cosa en un alcance dado.

#### [On Soft Scope](@id on-soft-scope)

Hemos cubierto todas las reglas del ámbito local, pero antes de concluir esta sección, quizás se deberían decir algunas palabras sobre por qué el caso ambiguo del ámbito suave se maneja de manera diferente en contextos interactivos y no interactivos. Hay dos preguntas obvias que se podrían hacer:

1. ¿Por qué no funciona simplemente como el REPL en todas partes?
2. ¿Por qué no funciona simplemente como en los archivos en todas partes? ¿Y tal vez omitir la advertencia?

En Julia ≤ 0.6, todos los ámbitos globales funcionaban como el REPL actual: cuando `x = <valor>` ocurría en un bucle (o `try`/`catch`, o cuerpo de `struct`) pero fuera de un cuerpo de función (o bloque `let` o comprensión), se decidía en función de si se definía un global llamado `x` o no si `x` debería ser local al bucle. Este comportamiento tiene la ventaja de ser intuitivo y conveniente, ya que se aproxima al comportamiento dentro de un cuerpo de función lo más posible. En particular, facilita mover código de un cuerpo de función al REPL y viceversa al intentar depurar el comportamiento de una función. Sin embargo, tiene algunas desventajas. Primero, es un comportamiento bastante complejo: muchas personas a lo largo de los años se confundieron con este comportamiento y se quejaron de que era complicado y difícil tanto de explicar como de entender. Punto justo. Segundo, y posiblemente peor, es que es malo para la programación "a gran escala". Cuando ves un pequeño fragmento de código en un lugar como este, es bastante claro lo que está sucediendo:

```julia
s = 0
for i = 1:10
    s += i
end
```

Obviamente, la intención es modificar la variable global existente `s`. ¿Qué más podría significar? Sin embargo, no todo el código del mundo real es tan corto o tan claro. Encontramos que el código como el siguiente a menudo ocurre en la naturaleza:

```julia
x = 123

# much later
# maybe in a different file

for i = 1:10
    x = "hello"
    println(x)
end

# much later
# maybe in yet another file
# or maybe back in the first one where `x = 123`

y = x + 234
```

No está tan claro qué debería suceder aquí. Dado que `x + "hello"` es un error de método, parece probable que la intención sea que `x` sea local al bucle `for`. Pero los valores en tiempo de ejecución y qué métodos existen no se pueden usar para determinar los ámbitos de las variables. Con el comportamiento de Julia ≤ 0.6, es especialmente preocupante que alguien haya escrito primero el bucle `for`, lo haya hecho funcionar bien, pero más tarde, cuando alguien más agrega un nuevo global lejos—posiblemente en un archivo diferente—el código cambia de significado y o bien falla ruidosamente o, peor aún, hace lo incorrecto en silencio. Este tipo de ["spooky action at a distance"](https://en.wikipedia.org/wiki/Action_at_a_distance_(computer_programming)) es algo que un buen diseño de lenguaje de programación debería prevenir.

Así que en Julia 1.0, simplificamos las reglas para el alcance: en cualquier alcance local, la asignación a un nombre que no era ya una variable local creaba una nueva variable local. Esto eliminó la noción de alcance suave por completo, así como también eliminó la posibilidad de acción espeluznante. Descubrimos y solucionamos un número significativo de errores debido a la eliminación del alcance suave, validando la elección de deshacerse de él. ¡Y hubo mucho regocijo! Bueno, no, en realidad no. Porque algunas personas estaban enojadas de que ahora tenían que escribir:

```julia
s = 0
for i = 1:10
    global s += i
end
```

¿Ves esa anotación `global` ahí? Horrible. Obviamente, esta situación no podría ser tolerada. Pero en serio, hay dos problemas principales con requerir `global` para este tipo de código de nivel superior:

1. Ya no es conveniente copiar y pegar el código desde el cuerpo de una función en el REPL para depurarlo; tienes que agregar anotaciones `global` y luego quitarlas nuevamente para volver.
2. Los principiantes escribirán este tipo de código sin el `global` y no tendrán idea de por qué su código no funciona; el error que obtienen es que `s` está indefinido, lo que no parece iluminar a nadie que comete este error.

A partir de Julia 1.5, este código funciona sin la anotación `global` en contextos interactivos como el REPL o los cuadernos de Jupyter (al igual que Julia 0.6) y en archivos y otros contextos no interactivos, imprime esta advertencia muy directa:

> La asignación a `s` en el ámbito suave es ambigua porque existe una variable global con el mismo nombre: `s` se tratará como una nueva variable local. Desambiguar utilizando `local s` para suprimir esta advertencia o `global s` para asignar a la variable global existente.


Esto aborda ambos problemas mientras preserva los beneficios de "programación a gran escala" del comportamiento 1.0: las variables globales no tienen un efecto extraño en el significado del código que puede estar lejos; en el REPL, la depuración por copia y pega funciona y los principiantes no tienen problemas; cada vez que alguien olvida una anotación `global` o accidentalmente oculta una global existente con una local en un ámbito suave, lo cual sería confuso de todos modos, recibe una advertencia clara y agradable.

Una propiedad importante de este diseño es que cualquier código que se ejecute en un archivo sin una advertencia se comportará de la misma manera en un REPL nuevo. Y, por el contrario, si tomas una sesión de REPL y la guardas en un archivo, si se comporta de manera diferente a como lo hizo en el REPL, entonces recibirás una advertencia.

### Let Blocks

`let` declaraciones crean un nuevo bloque de *alcance rígido* (ver arriba) e introducen nuevos enlaces de variables cada vez que se ejecutan. La variable no necesita ser asignada de inmediato:

```jldoctest
julia> var1 = let x
           for i in 1:5
               (i == 4) && (x = i; break)
           end
           x
       end
4
```

Mientras que las asignaciones pueden reasignar un nuevo valor a una ubicación de valor existente, `let` siempre crea una nueva ubicación. Esta diferencia generalmente no es importante y solo se puede detectar en el caso de variables que sobreviven a su alcance a través de cierres. La sintaxis de `let` acepta una serie de asignaciones y nombres de variables separadas por comas:

```jldoctest
julia> x, y, z = -1, -1, -1;

julia> let x = 1, z
           println("x: $x, y: $y") # x is local variable, y the global
           println("z: $z") # errors as z has not been assigned yet but is local
       end
x: 1, y: -1
ERROR: UndefVarError: `z` not defined in local scope
```

Las asignaciones se evalúan en orden, con cada lado derecho evaluado en el ámbito antes de que se haya introducido la nueva variable en el lado izquierdo. Por lo tanto, tiene sentido escribir algo como `let x = x` ya que las dos variables `x` son distintas y tienen almacenamiento separado. Aquí hay un ejemplo donde se necesita el comportamiento de `let`:

```jldoctest
julia> Fs = Vector{Any}(undef, 2); i = 1;

julia> while i <= 2
           Fs[i] = ()->i
           global i += 1
       end

julia> Fs[1]()
3

julia> Fs[2]()
3
```

Aquí creamos y almacenamos dos cierres que devuelven la variable `i`. Sin embargo, siempre es la misma variable `i`, por lo que los dos cierres se comportan de manera idéntica. Podemos usar `let` para crear un nuevo enlace para `i`:

```jldoctest
julia> Fs = Vector{Any}(undef, 2); i = 1;

julia> while i <= 2
           let i = i
               Fs[i] = ()->i
           end
           global i += 1
       end

julia> Fs[1]()
1

julia> Fs[2]()
2
```

Dado que la construcción `begin` no introduce un nuevo ámbito, puede ser útil usar un `let` sin argumentos para simplemente introducir un nuevo bloque de ámbito sin crear inmediatamente nuevas vinculaciones:

```jldoctest
julia> let
           local x = 1
           let
               local x = 2
           end
           x
       end
1
```

Dado que `let` introduce un nuevo bloque de alcance, la variable local interna `x` es diferente de la variable local externa `x`. Este ejemplo particular es equivalente a:

```jldoctest
julia> let x = 1
           let x = 2
           end
           x
       end
1
```

### Loops and Comprehensions

In loops and [comprehensions](@ref man-comprehensions), new variables introduced in their body scopes are freshly allocated for each loop iteration, as if the loop body were surrounded by a `let` block, as demonstrated by this example:

```jldoctest
julia> Fs = Vector{Any}(undef, 2);

julia> for j = 1:2
           Fs[j] = ()->j
       end

julia> Fs[1]()
1

julia> Fs[2]()
2
```

Una variable de iteración de un bucle `for` o de una comprensión es siempre una nueva variable:

```julia-repl enable_doctest_when_deprecation_warning_is_removed
julia> function f()
           i = 0
           for i = 1:3
               # empty
           end
           return i
       end;

julia> f()
0
```

Sin embargo, a veces es útil reutilizar una variable local existente como la variable de iteración. Esto se puede hacer de manera conveniente añadiendo la palabra clave `outer`:

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # empty
           end
           return i
       end;

julia> f()
3
```

## Constants

Un uso común de las variables es dar nombres a valores específicos y inmutables. Estas variables solo se asignan una vez. Esta intención se puede transmitir al compilador utilizando la palabra clave [`const`](@ref):

```jldoctest
julia> const e  = 2.71828182845904523536;

julia> const pi = 3.14159265358979323846;
```

Se pueden declarar múltiples variables en una sola declaración `const`:

```jldoctest
julia> const a, b = 1, 2
(1, 2)
```

La declaración `const` solo debe usarse en el ámbito global para variables globales. Es difícil para el compilador optimizar el código que involucra variables globales, ya que sus valores (o incluso sus tipos) pueden cambiar en casi cualquier momento. Si una variable global no cambiará, agregar una declaración `const` resuelve este problema de rendimiento.

Las constantes locales son bastante diferentes. El compilador puede determinar automáticamente cuándo una variable local es constante, por lo que las declaraciones de constantes locales no son necesarias y, de hecho, actualmente no son compatibles.

Las asignaciones especiales de nivel superior, como las realizadas por las palabras clave `function` y `struct`, son constantes por defecto.

Tenga en cuenta que `const` solo afecta la vinculación de la variable; la variable puede estar vinculada a un objeto mutable (como un arreglo), y ese objeto aún puede ser modificado. Además, cuando se intenta asignar un valor a una variable que se declara constante, los siguientes escenarios son posibles:

  * si un nuevo valor tiene un tipo diferente al tipo de la constante, se lanza un error:

```jldoctest
julia> const x = 1.0
1.0

julia> x = 1
ERROR: invalid redefinition of constant x
```

  * si un nuevo valor tiene el mismo tipo que la constante, se imprime una advertencia:

```jldoctest
julia> const y = 1.0
1.0

julia> y = 2.0
WARNING: redefinition of constant y. This may fail, cause incorrect answers, or produce other errors.
2.0
```

  * si una asignación no resultara en el cambio del valor de la variable, no se da ningún mensaje:

```jldoctest
julia> const z = 100
100

julia> z = 100
100
```

La última regla se aplica a los objetos inmutables incluso si la vinculación de la variable cambiaría, por ejemplo:

```julia-repl
julia> const s1 = "1"
"1"

julia> s2 = "1"
"1"

julia> pointer.([s1, s2], 1)
2-element Array{Ptr{UInt8},1}:
 Ptr{UInt8} @0x00000000132c9638
 Ptr{UInt8} @0x0000000013dd3d18

julia> s1 = s2
"1"

julia> pointer.([s1, s2], 1)
2-element Array{Ptr{UInt8},1}:
 Ptr{UInt8} @0x0000000013dd3d18
 Ptr{UInt8} @0x0000000013dd3d18
```

Sin embargo, para los objetos mutables, la advertencia se imprime como se esperaba:

```jldoctest
julia> const a = [1]
1-element Vector{Int64}:
 1

julia> a = [1]
WARNING: redefinition of constant a. This may fail, cause incorrect answers, or produce other errors.
1-element Vector{Int64}:
 1
```

Tenga en cuenta que, aunque a veces es posible, cambiar el valor de una variable `const` se desaconseja firmemente y se pretende solo por conveniencia durante el uso interactivo. Cambiar constantes puede causar varios problemas o comportamientos inesperados. Por ejemplo, si un método hace referencia a una constante y ya está compilado antes de que se cambie la constante, entonces podría seguir utilizando el viejo valor:

```jldoctest
julia> const x = 1
1

julia> f() = x
f (generic function with 1 method)

julia> f()
1

julia> x = 2
WARNING: redefinition of constant x. This may fail, cause incorrect answers, or produce other errors.
2

julia> f()
1
```

## [Typed Globals](@id man-typed-globals)

!!! compat "Julia 1.8"
    El soporte para globales tipados se agregó en Julia 1.8


Similar a ser declarados como constantes, los enlaces globales también pueden ser declarados para ser siempre de un tipo constante. Esto se puede hacer sin asignar un valor real utilizando la sintaxis `global x::T` o al momento de la asignación como `x::T = 123`.

```jldoctest
julia> x::Float64 = 2.718
2.718

julia> f() = x
f (generic function with 1 method)

julia> Base.return_types(f)
1-element Vector{Any}:
 Float64
```

Para cualquier asignación a un global, Julia primero intentará convertirlo al tipo apropiado usando [`convert`](@ref):

```jldoctest
julia> global y::Int

julia> y = 1.0
1.0

julia> y
1

julia> y = 3.14
ERROR: InexactError: Int64(3.14)
Stacktrace:
[...]
```

El tipo no necesita ser concreto, pero las anotaciones con tipos abstractos generalmente tienen poco beneficio en términos de rendimiento.

Una vez que se ha asignado un global o se ha establecido su tipo, no se permite cambiar el tipo de enlace:

```jldoctest
julia> x = 1
1

julia> global x::Int
ERROR: cannot set type for global x. It already has a value or is already set to a different type.
Stacktrace:
[...]
```
