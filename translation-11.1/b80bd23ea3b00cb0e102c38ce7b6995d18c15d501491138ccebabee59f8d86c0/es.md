# `EscapeAnalysis`

`Core.Compiler.EscapeAnalysis` es un módulo de utilidad del compilador que tiene como objetivo analizar la información de escape de [Julia's SSA-form IR](@ref Julia-SSA-form-IR), también conocido como `IRCode`.

Este análisis de escape tiene como objetivo:

  * aprovechar la semántica de alto nivel de Julia, especialmente razonar sobre escapes y aliasing a través de llamadas inter-procedurales
  * ser lo suficientemente versátil como para ser utilizado para varias optimizaciones, incluyendo [alias-aware SROA](https://github.com/JuliaLang/julia/pull/43888), [early `finalize` insertion](https://github.com/JuliaLang/julia/pull/44056), [copy-free `ImmutableArray` construction](https://github.com/JuliaLang/julia/pull/42465), la asignación de pila de objetos mutables, y así sucesivamente.
  * lograr una implementación simple basada en una implementación de análisis de flujo de datos completamente hacia atrás, así como un nuevo diseño de reticulado que combine propiedades de reticulado ortogonales.

## Try it out!

Puedes intentar el análisis de escape cargando el script de utilidad `EAUtils.jl` que define las entradas de conveniencia `code_escapes` y `@code_escapes` para fines de prueba y depuración:

```@repl EAUtils
let JULIA_DIR = normpath(Sys.BINDIR, "..", "share", "julia")
    # load `EscapeAnalysis` module to define the core analysis code
    include(normpath(JULIA_DIR, "base", "compiler", "ssair", "EscapeAnalysis", "EscapeAnalysis.jl"))
    using .EscapeAnalysis
    # load `EAUtils` module to define the utilities
    include(normpath(JULIA_DIR, "test", "compiler", "EscapeAnalysis", "EAUtils.jl"))
    using .EAUtils
end

mutable struct SafeRef{T}
    x::T
end
Base.getindex(x::SafeRef) = x.x;
Base.setindex!(x::SafeRef, v) = x.x = v;
Base.isassigned(x::SafeRef) = true;
get′(x) = isassigned(x) ? x[] : throw(x);

result = code_escapes((String,String,String,String)) do s1, s2, s3, s4
    r1 = Ref(s1)
    r2 = Ref(s2)
    r3 = SafeRef(s3)
    try
        s1 = get′(r1)
        ret = sizeof(s1)
    catch err
        global GV = err # will definitely escape `r1`
    end
    s2 = get′(r2)       # still `r2` doesn't escape fully
    s3 = get′(r3)       # still `r3` doesn't escape fully
    s4 = sizeof(s4)     # the argument `s4` doesn't escape here
    return s2, s3, s4
end
```

Los símbolos al lado de cada argumento de llamada y las declaraciones SSA representan el siguiente significado:

  * `◌` (plano): este valor no se analiza porque la información de escape de él no se utilizará de todos modos (cuando el objeto es `isbitstype`, por ejemplo)
  * `✓` (verde o cian): este valor nunca escapa (`has_no_escape(result.state[x])` se cumple), coloreado de azul si también tiene escape de argumento (`has_arg_escape(result.state[x])` se cumple)
  * `↑` (azul o amarillo): este valor puede escapar al llamador a través de la devolución (`has_return_escape(result.state[x])` se mantiene), coloreado de amarillo si también tiene una fuga lanzada no manejada (`has_thrown_escape(result.state[x])` se mantiene)
  * `X` (rojo): este valor puede escapar a algún lugar sobre el cual el análisis de escape no puede razonar, como escapes a una memoria global (`has_all_escape(result.state[x])` se cumple)
  * `*` (negrita): el estado de escape de este valor está entre el `ReturnEscape` y `AllEscape` en el orden parcial de [`EscapeInfo`](@ref Core.Compiler.EscapeAnalysis.EscapeInfo), coloreado de amarillo si tiene un escape lanzado no manejado también (`has_thrown_escape(result.state[x])` se cumple)
  * `′`: este valor tiene información adicional sobre el campo de objeto / elemento de matriz en su propiedad `AliasInfo`

La información de escape de cada argumento de llamada y valor SSA se puede inspeccionar programáticamente de la siguiente manera:

```@repl EAUtils
result.state[Core.Argument(3)] # get EscapeInfo of `s2`

result.state[Core.SSAValue(3)] # get EscapeInfo of `r3`
```

## Analysis Design

### Lattice Design

`EscapeAnalysis` se implementa como un [data-flow analysis](https://en.wikipedia.org/wiki/Data-flow_analysis) que trabaja en una red de [`x::EscapeInfo`](@ref Core.Compiler.EscapeAnalysis.EscapeInfo), que se compone de las siguientes propiedades:

  * `x.Analyzed::Bool`: no forma parte formalmente de la red, solo indica si `x` no ha sido analizado o no.
  * `x.ReturnEscape::BitSet`: registra declaraciones SSA donde `x` puede escapar al llamador a través de la devolución
  * `x.ThrownEscape::BitSet`: registra declaraciones SSA donde `x` puede ser lanzado como excepción (utilizado para el [exception handling](@ref EA-Exception-Handling) descrito a continuación)
  * `x.AliasInfo`: mantiene todos los posibles valores que pueden ser alias a campos o elementos de array de `x` (utilizado para el [alias analysis](@ref EA-Alias-Analysis) descrito a continuación)
  * `x.ArgEscape::Int` (no implementado aún): indica que se escapará al llamador a través de `setfield!` en el/los argumento(s)

Estos atributos se pueden combinar para crear un reticulado parcial que tiene una altura finita, dado el invariante de que un programa de entrada tiene un número finito de declaraciones, lo cual está asegurado por la semántica de Julia. La parte ingeniosa de este diseño de reticulado es que permite una implementación más simple de las operaciones de reticulado al permitir que manejen cada propiedad del reticulado por separado[^LatticeDesign].

### Backward Escape Propagation

Esta implementación de análisis de escape se basa en el algoritmo de flujo de datos descrito en el artículo[^MM02]. El análisis trabaja en la red de `EscapeInfo` y transiciona los elementos de la red desde la parte inferior hasta la parte superior hasta que cada elemento de la red converge a un punto fijo, manteniendo un conjunto de trabajo (conceptual) que contiene contadores de programa correspondientes a las declaraciones SSA restantes que deben ser analizadas. El análisis gestiona un único estado global que rastrea `EscapeInfo` de cada argumento y declaración SSA, pero también se debe tener en cuenta que cierta sensibilidad al flujo está codificada como contadores de programa registrados en la propiedad `ReturnEscape` de `EscapeInfo`, que se puede combinar con el análisis de dominación más adelante para razonar sobre la sensibilidad al flujo si es necesario.

Un diseño distintivo de este análisis de escape es que es completamente *hacia atrás*, es decir, la información de escape fluye *de los usos a las definiciones*. Por ejemplo, en el fragmento de código a continuación, EA primero analiza la declaración `return %1` e impone `ReturnEscape` sobre `%1` (correspondiente a `obj`), y luego analiza `%1 = %new(Base.RefValue{String, _2}))` y propaga el `ReturnEscape` impuesto sobre `%1` al argumento de llamada `_2` (correspondiente a `s`):

```@repl EAUtils
code_escapes((String,)) do s
    obj = Ref(s)
    return obj
end
```

La observación clave aquí es que este análisis hacia atrás permite que la información de escape fluya naturalmente a lo largo de la cadena de uso-definición en lugar de a través del flujo de control[^BackandForth]. Como resultado, este esquema permite una implementación simple del análisis de escape; por ejemplo, `PhiNode` puede ser manejado simplemente propagando la información de escape impuesta en un `PhiNode` a sus valores predecesores:

```@repl EAUtils
code_escapes((Bool, String, String)) do cnd, s, t
    if cnd
        obj = Ref(s)
    else
        obj = Ref(t)
    end
    return obj
end
```

### [Alias Analysis](@id EA-Alias-Analysis)

`EscapeAnalysis` implementa un análisis de campo hacia atrás para razonar sobre las escapadas impuestas en los campos de objeto con cierta precisión, y la propiedad `x.AliasInfo` de `x::EscapeInfo` existe para este propósito. Registra todos los valores posibles que pueden estar aliasados a los campos de `x` en los sitios de "uso", y luego la información de escape de esos valores registrados se propaga a los valores de campo reales más tarde en los sitios de "definición". Más específicamente, el análisis registra un valor que puede estar aliasado a un campo de objeto al analizar la llamada `getfield`, y luego propaga su información de escape al campo al analizar la expresión `%new(...)` o la llamada `setfield!`[^Dynamism].

```@repl EAUtils
code_escapes((String,)) do s
    obj = SafeRef("init")
    obj[] = s
    v = obj[]
    return v
end
```

En el ejemplo anterior, `ReturnEscape` impuesto sobre `%3` (correspondiente a `v`) *no* se propaga directamente a `%1` (correspondiente a `obj`), sino que `ReturnEscape` solo se propaga a `_2` (correspondiente a `s`). Aquí, `%3` se registra en la propiedad `AliasInfo` de `%1` ya que puede ser alias de el primer campo de `%1`, y luego, al analizar `Base.setfield!(%1, :x, _2)::String`, esa información de escape se propaga a `_2` pero no a `%1`.

Así que `EscapeAnalysis` rastrea qué elementos de IR pueden ser aliasados a través de una cadena `getfield`-`%new`/`setfield!` para analizar las escapadas de los campos de objeto, pero en realidad este análisis de alias necesita ser generalizado para manejar otros elementos de IR también. Esto se debe a que en IR de Julia el mismo objeto a veces se representa mediante diferentes elementos de IR y, por lo tanto, debemos asegurarnos de que esos diferentes elementos de IR que realmente pueden representar el mismo objeto compartan la misma información de escape. Los elementos de IR que devuelven el mismo objeto como su(s) operando(s), como `PiNode` y `typeassert`, pueden causar ese aliasing a nivel de IR y, por lo tanto, requieren que la información de escape impuesta sobre cualquiera de esos valores aliasados se comparta entre ellos. Más interesante aún, también es necesario para razonar correctamente sobre las mutaciones en `PhiNode`. Consideremos el siguiente ejemplo:

```@repl EAUtils
code_escapes((Bool, String,)) do cond, x
    if cond
        ϕ2 = ϕ1 = SafeRef("foo")
    else
        ϕ2 = ϕ1 = SafeRef("bar")
    end
    ϕ2[] = x
    y = ϕ1[]
    return y
end
```

`ϕ1 = %5` y `ϕ2 = %6` están aliasados y, por lo tanto, `ReturnEscape` impuesto sobre `%8 = Base.getfield(%6, :x)::String` (correspondiente a `y = ϕ1[]`) necesita ser propagado a `Base.setfield!(%5, :x, _3)::String` (correspondiente a `ϕ2[] = x`). Para que dicha información de escape se propague correctamente, el análisis debe reconocer que los *predecesores* de `ϕ1` y `ϕ2` también pueden estar aliasados y igualar su información de escape.

Una propiedad interesante de dicha información de aliasing es que no se conoce en el sitio de "uso", sino que solo se puede derivar en el sitio de "definición" (ya que el aliasing es conceptualmente equivalente a la asignación), y por lo tanto no se ajusta naturalmente a un análisis hacia atrás. Para propagar de manera eficiente la información de escape entre valores relacionados, EscapeAnalysis.jl utiliza un enfoque inspirado en el algoritmo de análisis de escape explicado en un viejo artículo de JVM[^JVM05]. Es decir, además de gestionar elementos de la red de escape, el análisis también mantiene un conjunto de alias "equi", un conjunto disjunto de argumentos y declaraciones SSA aliasados. El conjunto de alias gestiona valores que pueden estar aliasados entre sí y permite que la información de escape impuesta sobre cualquiera de esos valores aliasados se iguale entre ellos.

### [Array Analysis](@id EA-Array-Analysis)

El análisis de alias para los campos de objeto descrito anteriormente también se puede generalizar para analizar operaciones de arreglos. `EscapeAnalysis` implementa manejos para varias operaciones de arreglos primitivos de modo que puede propagar escapes a través de la cadena de uso-definición `arrayref`-`arrayset` y no escapa arreglos asignados de manera demasiado conservadora:

```@repl EAUtils
code_escapes((String,)) do s
    ary = Any[]
    push!(ary, SafeRef(s))
    return ary[1], length(ary)
end
```

En el ejemplo anterior, `EscapeAnalysis` entiende que `%20` y `%2` (correspondientes al objeto asignado `SafeRef(s)`) están aliasados a través de la cadena `arrayset`-`arrayref` y les impone `ReturnEscape`, pero no lo impone en el arreglo asignado `%1` (correspondiente a `ary`). `EscapeAnalysis` aún impone `ThrownEscape` en `ary` ya que también necesita tener en cuenta posibles escapes a través de `BoundsError`, pero también hay que notar que tal `ThrownEscape` no manejado a menudo puede ser ignorado al optimizar la asignación de `ary`.

Además, en los casos en que la información del índice del arreglo, así como las dimensiones del arreglo, se pueden conocer *precisamente*, `EscapeAnalysis` es capaz de razonar incluso sobre el aliasing "por elemento" a través de la cadena `arrayref`-`arrayset`, ya que `EscapeAnalysis` realiza un análisis de alias "por campo" para objetos:

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Vector{Any}(undef, 2)
    ary[1] = SafeRef(s)
    ary[2] = SafeRef(t)
    return ary[1], length(ary)
end
```

Tenga en cuenta que `ReturnEscape` solo se impone en `%2` (correspondiente a `SafeRef(s)`) pero no en `%4` (correspondiente a `SafeRef(t)`). Esto se debe a que la dimensión del array asignado y los índices involucrados en todas las operaciones `arrayref`/`arrayset` están disponibles como información constante y `EscapeAnalysis` puede entender que `%6` está aliasado a `%2` pero nunca está aliasado a `%4`. En este tipo de caso, los pases de optimización sucesivos podrán reemplazar `Base.arrayref(true, %1, 1)::Any` con `%2` (también conocido como "carga hacia adelante") y eventualmente eliminar la asignación del array `%1` por completo (también conocido como "reemplazo escalar").

Cuando se compara con el análisis de campos de objetos, donde un acceso a un campo de objeto puede ser analizado de manera trivial utilizando información de tipo derivada por inferencia, la dimensión de un arreglo no está codificada como información de tipo y, por lo tanto, necesitamos un análisis adicional para derivar esa información. `EscapeAnalysis` en este momento primero realiza un escaneo lineal simple adicional para analizar las dimensiones de los arreglos asignados antes de activar la rutina principal de análisis, de modo que el análisis de escape subsiguiente pueda analizar con precisión las operaciones en esos arreglos.

Sin embargo, tal análisis de alias "por elemento" tan preciso a menudo es difícil. Esencialmente, la principal dificultad inherente a los arreglos es que la dimensión del arreglo y el índice a menudo son no constantes:

  * el bucle a menudo produce índices de matriz no constantes y variantes del bucle
  * (el específico para vectores) el cambio de tamaño de la matriz modifica la dimensión de la matriz e invalida su constancia.

Hablemos de esas dificultades con ejemplos concretos.

En el siguiente ejemplo, `EscapeAnalysis` falla en el análisis de alias preciso ya que el índice en `Base.arrayset(false, %4, %8, %6)::Vector{Any}` no es (trivialmente) constante. Especialmente, `Any[nothing, nothing]` forma un bucle y llama a esa operación `arrayset` en un bucle, donde `%6` se representa como un valor de nodo ϕ (cuyo valor depende del flujo de control). Como resultado, `ReturnEscape` termina imponiéndose tanto en `%23` (correspondiente a `SafeRef(s)`) como en `%25` (correspondiente a `SafeRef(t)`), aunque idealmente queremos que se imponga solo en `%23` pero no en `%25`:

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Any[nothing, nothing]
    ary[1] = SafeRef(s)
    ary[2] = SafeRef(t)
    return ary[1], length(ary)
end
```

El siguiente ejemplo ilustra cómo el cambio de tamaño de un vector dificulta el análisis de alias preciso. La dificultad esencial es que la dimensión del arreglo asignado `%1` se inicializa primero como `0`, pero cambia con las dos llamadas `:jl_array_grow_end` posteriormente. `EscapeAnalysis` actualmente simplemente renuncia al análisis de alias preciso cada vez que encuentra operaciones de cambio de tamaño de arreglos y, por lo tanto, se impone `ReturnEscape` tanto en `%2` (correspondiente a `SafeRef(s)`) como en `%20` (correspondiente a `SafeRef(t)`):

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Any[]
    push!(ary, SafeRef(s))
    push!(ary, SafeRef(t))
    ary[1], length(ary)
end
```

Para abordar estas dificultades, necesitamos que la inferencia sea consciente de las dimensiones de los arreglos y propague las dimensiones de los arreglos de manera sensible al flujo[^ArrayDimension], así como también idear una buena representación de los valores variantes del bucle.

`EscapeAnalysis` en este momento cambia rápidamente a un análisis más impreciso que no rastrea información de índice precisa en casos en los que las dimensiones del arreglo o los índices son trivialmente no constantes. El cambio se puede implementar naturalmente como una operación de unión de reticulado de la propiedad `EscapeInfo.AliasInfo` en el marco de análisis de flujo de datos.

### [Exception Handling](@id EA-Exception-Handling)

También vale la pena señalar cómo `EscapeAnalysis` maneja posibles escapes a través de excepciones. A primera vista, parece suficiente propagar la información de escape impuesta sobre el objeto `:the_exception` a todos los valores que pueden ser lanzados en un bloque `try` correspondiente. Pero en realidad, hay varias otras formas de acceder al objeto de excepción en Julia, como `Base.current_exceptions` y `rethrow`. Por ejemplo, el análisis de escape necesita tener en cuenta el posible escape de `r` en el ejemplo a continuación:

```@repl EAUtils
const GR = Ref{Any}();
@noinline function rethrow_escape!()
    try
        rethrow()
    catch err
        GR[] = err
    end
end;
get′(x) = isassigned(x) ? x[] : throw(x);

code_escapes() do
    r = Ref{String}()
    local t
    try
        t = get′(r)
    catch err
        t = typeof(err)   # `err` (which `r` aliases to) doesn't escape here
        rethrow_escape!() # but `r` escapes here
    end
    return t
end
```

Requiere un análisis global para razonar correctamente sobre todas las posibles salidas a través de las interfaces de excepción existentes. Por ahora, siempre propagamos la información de escape más alta a todos los objetos que podrían lanzarse de manera conservadora, ya que un análisis adicional podría no valer la pena realizarlo dado que el manejo de excepciones y las rutas de error generalmente no necesitan ser muy sensibles al rendimiento, y además, las optimizaciones de las rutas de error podrían ser muy ineficaces de todos modos, ya que a menudo están incluso "no optimizadas" intencionalmente por razones de latencia.

La propiedad `x.ThrownEscape` de `x::EscapeInfo` registra las declaraciones SSA donde `x` puede ser lanzado como una excepción. Usando esta información, `EscapeAnalysis` puede propagar posibles escapes a través de excepciones de manera limitada solo a aquellos que pueden ser lanzados en cada región `try`:

```@repl EAUtils
result = code_escapes((String,String)) do s1, s2
    r1 = Ref(s1)
    r2 = Ref(s2)
    local ret
    try
        s1 = get′(r1)
        ret = sizeof(s1)
    catch err
        global GV = err # will definitely escape `r1`
    end
    s2 = get′(r2)       # still `r2` doesn't escape fully
    return s2
end
```

## Analysis Usage

`analyze_escapes` es el punto de entrada para analizar la información de escape de los elementos SSA-IR.

La mayoría de las optimizaciones como SROA (`sroa_pass!`) son más efectivas cuando se aplican a un código fuente optimizado que el paso de inlining (`ssa_inlining_pass!`) ha simplificado al resolver llamadas inter-procedimentales y expandir las fuentes de los llamados. En consecuencia, `analyze_escapes` también puede analizar IR posterior al inlining y recopilar información sobre escapes que es útil para ciertas optimizaciones relacionadas con la memoria.

Sin embargo, dado que ciertos pases de optimización como la inlining pueden cambiar los flujos de control y eliminar código muerto, pueden romper la validez inter-procedimental de la información de escape. En particular, para recopilar información de escape válida inter-procedimentalmente, necesitamos analizar un IR previo a la inlining.

Debido a esta razón, `analyze_escapes` puede analizar `IRCode` en cualquier etapa de optimización a nivel de Julia, y especialmente, se supone que debe usarse en las siguientes dos etapas:

  * `IPO EA`: analizar IR previo a la inlining para generar caché de información de escape válida para IPO
  * `Local EA`: analizar IR post-inlining para recopilar información de escape localmente válida

La información de escape derivada por `IPO EA` se transforma en la estructura de datos `ArgEscapeCache` y se almacena en caché globalmente. Al pasar un callback apropiado `get_escape_cache` a `analyze_escapes`, el análisis de escape puede mejorar la precisión del análisis al utilizar información interprocedimental en caché de llamadas no inlinadas que ha sido derivada por el anterior `IPO EA`. Más interesante aún, también es válido utilizar la información de escape de `IPO EA` para la inferencia de tipos, por ejemplo, la precisión de la inferencia puede mejorarse formando `Const`/`PartialStruct`/`MustAlias` de un objeto mutable.

```@docs
Core.Compiler.EscapeAnalysis.analyze_escapes
Core.Compiler.EscapeAnalysis.EscapeState
Core.Compiler.EscapeAnalysis.EscapeInfo
```

---

[^LatticeDesign]: Our type inference implementation takes the alternative approach, where each lattice property is represented by a special lattice element type object. It turns out that it started to complicate implementations of the lattice operations mainly because it often requires conversion rules between each lattice element type object. And we are working on [overhauling our type inference lattice implementation](https://github.com/JuliaLang/julia/pull/42596) with `EscapeInfo`-like lattice design.

[^MM02]: *A Graph-Free approach to Data-Flow Analysis*.      Markas Mohnen, 2002, April.      [https://api.semanticscholar.org/CorpusID:28519618](https://api.semanticscholar.org/CorpusID:28519618).

[^BackandForth]: Our type inference algorithm in contrast is implemented as a forward analysis, because type information usually flows from "definition" to "usage" and it is more natural and effective to propagate such information in a forward way.

[^Dynamism]: In some cases, however, object fields can't be analyzed precisely. For example, object may escape to somewhere `EscapeAnalysis` can't account for possible memory effects on it, or fields of the objects simply can't be known because of the lack of type information. In such cases `AliasInfo` property is raised to the topmost element within its own lattice order, and it causes succeeding field analysis to be conservative and escape information imposed on fields of an unanalyzable object to be propagated to the object itself.

[^JVM05]: *Escape Analysis in the Context of Dynamic Compilation and Deoptimization*.       Thomas Kotzmann and Hanspeter Mössenböck, 2005, June.       [https://dl.acm.org/doi/10.1145/1064979.1064996](https://dl.acm.org/doi/10.1145/1064979.1064996).

[^ArrayDimension]: Otherwise we will need yet another forward data-flow analysis on top of the escape analysis.
