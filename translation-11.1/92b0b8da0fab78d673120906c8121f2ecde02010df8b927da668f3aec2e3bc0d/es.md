# Julia SSA-form IR

Julia utiliza una representación intermedia de asignación única estática ([SSA IR](https://en.wikipedia.org/wiki/Static_single-assignment_form)) para realizar optimizaciones. Esta IR es diferente de LLVM IR y es única de Julia. Permite optimizaciones específicas de Julia.

1. Los bloques básicos (regiones sin flujo de control) están anotados explícitamente.
2. si/else y bucles se convierten en declaraciones `goto`.
3. las líneas con múltiples operaciones se dividen en múltiples líneas al introducir variables.

Por ejemplo, el siguiente código de Julia:

```julia
function foo(x)
    y = sin(x)
    if x > 5.0
        y = y + cos(x)
    end
    return exp(2) + y
end
```

cuando se llama con un argumento `Float64` se traduce en:

```julia
using InteractiveUtils
@code_typed foo(1.0)
```

```llvm
CodeInfo(
1 ─ %1 = invoke Main.sin(x::Float64)::Float64
│   %2 = Base.lt_float(x, 5.0)::Bool
└──      goto #3 if not %2
2 ─ %4 = invoke Main.cos(x::Float64)::Float64
└── %5 = Base.add_float(%1, %4)::Float64
3 ┄ %6 = φ (#2 => %5, #1 => %1)::Float64
│   %7 = Base.add_float(7.38905609893065, %6)::Float64
└──      return %7
) => Float64
```

En este ejemplo, podemos ver todos estos cambios.

1. El primer bloque básico es todo en

```llvm
1 ─ %1 = invoke Main.sin(x::Float64)::Float64
│   %2 = Base.lt_float(x, 5.0)::Bool
└──      goto #3 if not %2
```

2. La declaración `if` se traduce en `goto #3 if not %2`, que va al tercer bloque básico si no se cumple `x>5` y, de lo contrario, va al segundo bloque básico.
3. `%2` es un valor SSA introducido para representar `x > 5`.

## Background

A partir de Julia 0.7, partes del compilador utilizan una nueva representación intermedia (IR) [SSA-form](https://en.wikipedia.org/wiki/Static_single_assignment_form). Históricamente, el compilador generaba directamente IR de LLVM a partir de una forma reducida del AST de Julia. Esta forma tenía la mayoría de las abstracciones sintácticas eliminadas, pero aún se parecía mucho a un árbol de sintaxis abstracta. Con el tiempo, para facilitar las optimizaciones, se introdujeron valores SSA en esta IR y la IR fue linealizada (es decir, convertida en una forma donde los argumentos de función solo podían ser valores SSA o constantes). Sin embargo, los valores no SSA (slots) permanecieron en la IR debido a la falta de nodos Phi en la IR (necesarios para los retrocesos y la re-fusión del flujo de control condicional). Esto anuló gran parte de la utilidad de la representación en forma SSA al realizar optimizaciones de medio término. Se realizó un esfuerzo heroico para hacer que estas optimizaciones funcionaran sin una representación completa en forma SSA, pero la falta de tal representación demostró ser finalmente prohibitiva.

## Categories of IR nodes

La representación IR de SSA tiene cuatro categorías de nodos IR: nodos Phi, Pi, PhiC y Upsilon (los dos últimos solo se utilizan para el manejo de excepciones).

### Phi nodes and Pi nodes

Los nodos Phi son parte de la abstracción SSA genérica (consulta el enlace anterior si no estás familiarizado con el concepto). En el IR de Julia, estos nodos se representan como:

```
struct PhiNode
    edges::Vector{Int32}
    values::Vector{Any}
end
```

donde aseguramos que ambos vectores siempre tengan la misma longitud. En la representación canónica (la que maneja codegen y el intérprete), los valores de los bordes indican números de declaración de origen (es decir, si el borde tiene una entrada de `15`, debe haber un `goto`, `gotoifnot` o una caída implícita desde la declaración `15` que apunte a este nodo phi). Los valores son ya sea valores SSA o constantes. También es posible que un valor no esté asignado si la variable no fue definida en este camino. Sin embargo, las verificaciones de indefinición se insertan explícitamente y se representan como booleanos después de las optimizaciones de medio término, por lo que los generadores de código pueden asumir que cualquier uso de un nodo Phi tendrá un valor asignado en la ranura correspondiente. También es legal que el mapeo esté incompleto, es decir, que un nodo Phi tenga bordes entrantes faltantes. En ese caso, debe garantizarse dinámicamente que el valor correspondiente no será utilizado.

Tenga en cuenta que SSA utiliza semánticamente ocurrir después del terminador del predecesor correspondiente ("en el borde"). En consecuencia, si múltiples nodos Phi aparecen al inicio de un bloque básico, se ejecutan simultáneamente. Esto significa que en el siguiente fragmento de IR, si venimos del bloque `23`, `%46` tomará el valor asociado a `%45` *antes* de que entremos en este bloque.

```julia
%45 = φ (#18 => %23, #23 => %50)
%46 = φ (#18 => 1.0, #23 => %45)
```

PiNodes codifican información probada de manera estática que puede ser asumida implícitamente en bloques básicos dominados por un nodo pi dado. Son conceptualmente equivalentes a la técnica introducida en el artículo [ABCD: Eliminating Array Bounds Checks on Demand](https://dl.acm.org/citation.cfm?id=358438.349342) o los nodos de información de predicado en LLVM. Para ver cómo funcionan, considera, por ejemplo.

```julia
%x::Union{Int, Float64} # %x is some Union{Int, Float64} typed ssa value
if isa(x, Int)
    # use x
else
    # use x
end
```

Podemos realizar la inserción de predicados y convertir esto en:

```julia
%x::Union{Int, Float64} # %x is some Union{Int, Float64} typed ssa value
if isa(x, Int)
    %x_int = PiNode(x, Int)
    # use %x_int
else
    %x_float = PiNode(x, Float64)
    # use %x_float
end
```

Los nodos Pi generalmente se ignoran en el intérprete, ya que no tienen ningún efecto en los valores, pero a veces pueden llevar a la generación de código en el compilador (por ejemplo, para cambiar de una representación de división de unión implícita a una representación sin caja simple). La principal utilidad de los nodos Pi proviene del hecho de que las condiciones de ruta de los valores se pueden acumular simplemente mediante el recorrido de la cadena de uso-definición que generalmente se realiza para la mayoría de las optimizaciones que se preocupan por estas condiciones de todos modos.

### PhiC nodes and Upsilon nodes

El manejo de excepciones complica moderadamente la historia de SSA, porque el manejo de excepciones introduce bordes de flujo de control adicionales en el IR a través de los cuales se deben rastrear los valores. Un enfoque para hacerlo, que sigue LLVM, es convertir las llamadas que pueden lanzar excepciones en terminadores de bloques básicos y agregar un borde de flujo de control explícito al controlador de excepciones:

```
invoke @function_that_may_throw() to label %regular unwind to %catch

regular:
# Control flow continues here

catch:
# Exceptions go here
```

Sin embargo, esto es problemático en un lenguaje como Julia, donde al inicio del pipeline de optimización, no sabemos qué llamadas lanzan excepciones. Tendríamos que asumir de manera conservadora que cada llamada (que en Julia es cada declaración) lanza una excepción. Esto tendría varios efectos negativos. Por un lado, reduciría esencialmente el alcance de cada bloque básico a una sola llamada, lo que anularía el propósito de realizar operaciones a nivel de bloque básico. Por otro lado, cada bloque básico de captura tendría `n*m` argumentos de nodo phi (`n`, el número de declaraciones en la región crítica, `m` el número de valores vivos a través del bloque de captura).

Para sortear esto, usamos una combinación de nodos `Upsilon` y `PhiC` (la C significa `catch`, escrita como `φᶜ` en el impresor de IR, porque el subíndice c en unicode no está disponible). Hay varias formas de pensar en estos nodos, pero quizás la más fácil es pensar en cada `PhiC` como una carga de un slot único de almacenamiento-múltiple, lectura-una-vez, siendo `Upsilon` la operación de almacenamiento correspondiente. El `PhiC` tiene una lista de operandos de todos los nodos upsilon que almacenan en su slot implícito. Sin embargo, los nodos `Upsilon` no registran a qué nodo `PhiC` almacenan. Esto se hace para una integración más natural con el resto del IR SSA. Por ejemplo, si no hay más usos de un nodo `PhiC`, es seguro eliminarlo, y lo mismo es cierto para un nodo `Upsilon`. En la mayoría de los pases de IR, los nodos `PhiC` pueden ser tratados como nodos `Phi`. Se pueden seguir las cadenas de uso-def a través de ellos, y pueden ser elevados a nuevos nodos `PhiC` y nuevos nodos `Upsilon` (en los mismos lugares que los nodos `Upsilon` originales). El resultado de este esquema es que el número de nodos `Upsilon` (y argumentos `PhiC`) es proporcional al número de valores asignados a una variable particular (antes de la conversión SSA), en lugar del número de declaraciones en la región crítica.

Para ver este esquema en acción, considera la función

```julia
@noinline opaque() = invokelatest(identity, nothing) # Something opaque
function foo()
    local y
    x = 1
    try
        y = 2
        opaque()
        y = 3
        error()
    catch
    end
    (x, y)
end
```

El IR correspondiente (con tipos irrelevantes eliminados) es:

```
1 ─       nothing::Nothing
2 ─ %2  = $(Expr(:enter, #4))
3 ─ %3  = ϒ (false)
│   %4  = ϒ (#undef)
│   %5  = ϒ (1)
│   %6  = ϒ (true)
│   %7  = ϒ (2)
│         invoke Main.opaque()::Any
│   %9  = ϒ (true)
│   %10 = ϒ (3)
│         invoke Main.error()::Union{}
└──       $(Expr(:unreachable))::Union{}
4 ┄ %13 = φᶜ (%3, %6, %9)::Bool
│   %14 = φᶜ (%4, %7, %10)::Core.Compiler.MaybeUndef(Int64)
│   %15 = φᶜ (%5)::Core.Const(1)
└──       $(Expr(:leave, Core.SSAValue(2)))
5 ─       $(Expr(:pop_exception, :(%2)))::Any
│         $(Expr(:throw_undef_if_not, :y, :(%13)))::Any
│   %19 = Core.tuple(%15, %14)
└──       return %19
```

Nota en particular que cada valor que vive en la región crítica recibe un nodo upsilon en la parte superior de la región crítica. Esto se debe a que los bloques catch se consideran tener un borde de flujo de control invisible desde fuera de la función. Como resultado, ningún valor SSA domina los bloques catch, y todos los valores entrantes tienen que pasar a través de un nodo `φᶜ`.

## Main SSA data structure

La estructura de datos principal `SSAIR` merece ser discutida. Se inspira en LLVM y en el IR B3 de Webkit. El núcleo de la estructura de datos es un vector plano de declaraciones. Cada declaración se asigna implícitamente un valor SSA basado en su posición en el vector (es decir, el resultado de la declaración en el índice 1 se puede acceder usando `SSAValue(1)`, etc.). Para cada valor SSA, además mantenemos su tipo. Dado que los valores SSA se asignan definicionalmente solo una vez, este tipo también es el tipo de resultado de la expresión en el índice correspondiente. Sin embargo, aunque esta representación es bastante eficiente (ya que las asignaciones no necesitan ser codificadas explícitamente), por supuesto, tiene la desventaja de que el orden es semánticamente significativo, por lo que los reordenamientos e inserciones cambian los números de las declaraciones. Además, no mantenemos listas de uso (es decir, es imposible caminar desde una definición a todos sus usos sin calcular explícitamente este mapa; sin embargo, las listas de definiciones son triviales ya que se puede buscar la declaración correspondiente desde el índice), por lo que la operación RAUW (reemplazar-todos-los-usos-con) al estilo LLVM no está disponible.

En su lugar, hacemos lo siguiente:

  * Mantenemos un búfer separado de nodos para insertar (incluyendo la posición para insertarlos, el tipo del valor correspondiente y el nodo en sí). Estos nodos están numerados por su ocurrencia en el búfer de inserción, lo que permite que sus valores sean utilizados inmediatamente en otros lugares del IR (es decir, si hay 12 declaraciones en la lista de declaraciones original, la primera nueva declaración será accesible como `SSAValue(13)`).
  * Las operaciones de estilo RAUW se realizan estableciendo el índice de declaración correspondiente al valor de reemplazo.
  * Las declaraciones se eliminan estableciendo la declaración correspondiente a `nada` (esto es esencialmente solo una convención de caso especial de lo anterior).
  * Si hay algún uso de la declaración que se está borrando, se establecerán en `nada`.

Hay una función `compact!` que compacta la estructura de datos anterior realizando la inserción de nodos en el lugar apropiado, propagación trivial de copias y renombrado de usos a cualquier valor SSA cambiado. Sin embargo, la parte ingeniosa de este esquema es que esta compactación se puede hacer de manera perezosa como parte del pase subsiguiente. La mayoría de los pases de optimización necesitan recorrer toda la lista de declaraciones, realizando análisis o modificaciones en el camino. Proporcionamos un iterador `IncrementalCompact` que se puede usar para iterar sobre la lista de declaraciones. Realizará cualquier compactación necesaria y devolverá el nuevo índice del nodo, así como el nodo mismo. Es legal en este punto recorrer cadenas de definición-uso, así como hacer cualquier modificación o eliminación al IR (sin embargo, se desaconsejan las inserciones).

La idea detrás de este arreglo es que, dado que las pasadas de optimización necesitan acceder a la memoria correspondiente de todos modos y incurrir en la penalización de acceso a la memoria correspondiente, realizar el trabajo adicional de mantenimiento debería tener un costo comparativamente bajo (y ahorrar el costo de mantener estas estructuras de datos durante la modificación de IR).
