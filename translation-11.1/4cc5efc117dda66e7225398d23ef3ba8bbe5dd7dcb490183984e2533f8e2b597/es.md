# More about types

Si has utilizado Julia durante un tiempo, entiendes el papel fundamental que juegan los tipos. Aquí intentamos profundizar, centrándonos particularmente en [Parametric Types](@ref).

## Types and sets (and `Any` and `Union{}`/`Bottom`)

Es quizás más fácil concebir el sistema de tipos de Julia en términos de conjuntos. Mientras que los programas manipulan valores individuales, un tipo se refiere a un conjunto de valores. Esto no es lo mismo que una colección; por ejemplo, un [`Set`](@ref) de valores es en sí mismo un único valor de `Set`. Más bien, un tipo describe un conjunto de *valores posibles*, expresando incertidumbre sobre qué valor tenemos.

Un tipo *concreto* `T` describe el conjunto de valores cuyo tag directo, como lo devuelve la función [`typeof`](@ref), es `T`. Un tipo *abstracto* describe algún conjunto de valores posiblemente más grande.

[`Any`](@ref) describe el universo entero de valores posibles. [`Integer`](@ref) es un subconjunto de `Any` que incluye `Int`, [`Int8`](@ref), y otros tipos concretos. Internamente, Julia también hace un uso intensivo de otro tipo conocido como `Bottom`, que también se puede escribir como `Union{}`. Esto corresponde al conjunto vacío.

Los tipos de Julia admiten las operaciones estándar de la teoría de conjuntos: puedes preguntar si `T1` es un "subconjunto" (subtipo) de `T2` con `T1 <: T2`. Del mismo modo, puedes intersectar dos tipos usando [`typeintersect`](@ref), tomar su unión con [`Union`](@ref), y calcular un tipo que contenga su unión con [`typejoin`](@ref):

```jldoctest
julia> typeintersect(Int, Float64)
Union{}

julia> Union{Int, Float64}
Union{Float64, Int64}

julia> typejoin(Int, Float64)
Real

julia> typeintersect(Signed, Union{UInt8, Int8})
Int8

julia> Union{Signed, Union{UInt8, Int8}}
Union{UInt8, Signed}

julia> typejoin(Signed, Union{UInt8, Int8})
Integer

julia> typeintersect(Tuple{Integer, Float64}, Tuple{Int, Real})
Tuple{Int64, Float64}

julia> Union{Tuple{Integer, Float64}, Tuple{Int, Real}}
Union{Tuple{Int64, Real}, Tuple{Integer, Float64}}

julia> typejoin(Tuple{Integer, Float64}, Tuple{Int, Real})
Tuple{Integer, Real}
```

Mientras que estas operaciones pueden parecer abstractas, están en el corazón de Julia. Por ejemplo, la selección de métodos se implementa recorriendo los elementos en una lista de métodos hasta llegar a uno para el cual el tipo de la tupla de argumentos es un subtipo de la firma del método. Para que este algoritmo funcione, es importante que los métodos estén ordenados por su especificidad, y que la búsqueda comience con los métodos más específicos. En consecuencia, Julia también implementa un orden parcial en los tipos; esto se logra mediante una funcionalidad que es similar a `<:`, pero con diferencias que se discutirán a continuación.

## UnionAll types

El sistema de tipos de Julia también puede expresar una *unión iterada* de tipos: una unión de tipos sobre todos los valores de alguna variable. Esto es necesario para describir tipos paramétricos donde los valores de algunos parámetros no son conocidos.

Por ejemplo, [`Array`](@ref) tiene dos parámetros como en `Array{Int,2}`. Si no supiéramos el tipo de elemento, podríamos escribir `Array{T,2} where T`, que es la unión de `Array{T,2}` para todos los valores de `T`: `Union{Array{Int8,2}, Array{Int16,2}, ...}`.

Tal tipo está representado por un objeto `UnionAll`, que contiene una variable (`T` en este ejemplo, de tipo `TypeVar`), y un tipo envuelto (`Array{T,2}` en este ejemplo).

Considere los siguientes métodos:

```julia
f1(A::Array) = 1
f2(A::Array{Int}) = 2
f3(A::Array{T}) where {T<:Any} = 3
f4(A::Array{Any}) = 4
```

La firma - como se describe en [Function calls](@ref Function-calls) - de `f3` es un tipo `UnionAll` que envuelve un tipo de tupla: `Tuple{typeof(f3), Array{T}} donde T`. Todos menos `f4` se pueden llamar con `a = [1,2]`; todos menos `f2` se pueden llamar con `b = Any[1,2]`.

Veamos estos tipos con un poco más de detalle:

```jldoctest
julia> dump(Array)
UnionAll
  var: TypeVar
    name: Symbol T
    lb: Union{}
    ub: Any
  body: UnionAll
    var: TypeVar
      name: Symbol N
      lb: Union{}
      ub: Any
    body: Array{T, N} <: DenseArray{T, N}
      ref::MemoryRef{T}
      size::NTuple{N, Int64}
```

Esto indica que `Array` en realidad nombra un tipo `UnionAll`. Hay un tipo `UnionAll` para cada parámetro, anidado. La sintaxis `Array{Int,2}` es equivalente a `Array{Int}{2}`; internamente, cada `UnionAll` se instancia con un valor de variable particular, uno a la vez, comenzando por el más externo. Esto da un significado natural a la omisión de parámetros de tipo finales; `Array{Int}` da un tipo equivalente a `Array{Int,N} donde N`.

Un `TypeVar` no es en sí mismo un tipo, sino que debe considerarse parte de la estructura de un tipo `UnionAll`. Las variables de tipo tienen límites inferiores y superiores en sus valores (en los campos `lb` y `ub`). El símbolo `name` es puramente cosmético. Internamente, los `TypeVar` se comparan por dirección, por lo que se definen como tipos mutables para garantizar que se puedan distinguir las "diferentes" variables de tipo. Sin embargo, por convención, no deben ser mutadas.

Se pueden construir `TypeVar`s manualmente:

```jldoctest
julia> TypeVar(:V, Signed, Real)
Signed<:V<:Real
```

Hay versiones convenientes que te permiten omitir cualquiera de estos argumentos excepto el símbolo `name`.

La sintaxis `Array{T} where T<:Integer` se reduce a

```julia
let T = TypeVar(:T,Integer)
    UnionAll(T, Array{T})
end
```

por lo que rara vez es necesario construir un `TypeVar` manualmente (de hecho, esto debe evitarse).

## Free variables

El concepto de una variable de tipo *libre* es extremadamente importante en el sistema de tipos. Decimos que una variable `V` es libre en el tipo `T` si `T` no contiene el `UnionAll` que introduce la variable `V`. Por ejemplo, el tipo `Array{Array{V} donde V<:Integer}` no tiene variables libres, pero la parte `Array{V}` dentro de él sí tiene una variable libre, `V`.

Un tipo con variables libres no es, en cierto sentido, realmente un tipo en absoluto. Considera el tipo `Array{Array{T}} where T`, que se refiere a todos los arreglos homogéneos de arreglos. El tipo interno `Array{T}`, visto por sí mismo, podría parecer referirse a cualquier tipo de arreglo. Sin embargo, cada elemento del arreglo externo debe tener el *mismo* tipo de arreglo, por lo que `Array{T}` no puede referirse a cualquier arreglo viejo. Se podría decir que `Array{T}` "ocurre" efectivamente múltiples veces, y `T` debe tener el mismo valor cada "vez".

Por esta razón, la función `jl_has_free_typevars` en la API de C es muy importante. Los tipos para los cuales devuelve verdadero no darán respuestas significativas en la subtipificación y otras funciones de tipo.

## TypeNames

Los siguientes dos [`Array`](@ref) tipos son funcionalmente equivalentes, pero se imprimen de manera diferente:

```jldoctest
julia> TV, NV = TypeVar(:T), TypeVar(:N)
(T, N)

julia> Array
Array

julia> Array{TV, NV}
Array{T, N}
```

Estos se pueden distinguir examinando el campo `name` del tipo, que es un objeto del tipo `TypeName`:

```julia-repl
julia> dump(Array{Int,1}.name)
TypeName
  name: Symbol Array
  module: Module Core
  names: empty SimpleVector
  wrapper: UnionAll
    var: TypeVar
      name: Symbol T
      lb: Union{}
      ub: Any
    body: UnionAll
      var: TypeVar
        name: Symbol N
        lb: Union{}
        ub: Any
      body: Array{T, N} <: DenseArray{T, N}
  cache: SimpleVector
    ...

  linearcache: SimpleVector
    ...

  hash: Int64 -7900426068641098781
  mt: MethodTable
    name: Symbol Array
    defs: Nothing nothing
    cache: Nothing nothing
    max_args: Int64 0
    module: Module Core
    : Int64 0
    : Int64 0
```

En este caso, el campo relevante es `wrapper`, que mantiene una referencia al tipo de nivel superior utilizado para crear nuevos tipos de `Array`.

```julia-repl
julia> pointer_from_objref(Array)
Ptr{Cvoid} @0x00007fcc7de64850

julia> pointer_from_objref(Array.body.body.name.wrapper)
Ptr{Cvoid} @0x00007fcc7de64850

julia> pointer_from_objref(Array{TV,NV})
Ptr{Cvoid} @0x00007fcc80c4d930

julia> pointer_from_objref(Array{TV,NV}.name.wrapper)
Ptr{Cvoid} @0x00007fcc7de64850
```

El campo `wrapper` de [`Array`](@ref) apunta a sí mismo, pero para `Array{TV,NV}` apunta de vuelta a la definición original del tipo.

¿Qué pasa con los otros campos? `hash` asigna un entero a cada tipo. Para examinar el campo `cache`, es útil elegir un tipo que se use menos que Array. Primero, creemos nuestro propio tipo:

```jldoctest
julia> struct MyType{T,N} end

julia> MyType{Int,2}
MyType{Int64, 2}

julia> MyType{Float32, 5}
MyType{Float32, 5}
```

Cuando instancias un tipo paramétrico, cada tipo concreto se guarda en una caché de tipos (`MyType.body.body.name.cache`). Sin embargo, las instancias que contienen variables de tipo libres no se almacenan en caché.

## Tuple types

Los tipos de tuplas constituyen un caso especial interesante. Para que el despacho funcione en declaraciones como `x::Tuple`, el tipo debe ser capaz de acomodar cualquier tupla. Verifiquemos los parámetros:

```jldoctest
julia> Tuple
Tuple

julia> Tuple.parameters
svec(Vararg{Any})
```

A diferencia de otros tipos, los tipos de tuplas son covariantes en sus parámetros, por lo que esta definición permite que `Tuple` coincida con cualquier tipo de tupla:

```jldoctest
julia> typeintersect(Tuple, Tuple{Int,Float64})
Tuple{Int64, Float64}

julia> typeintersect(Tuple{Vararg{Any}}, Tuple{Int,Float64})
Tuple{Int64, Float64}
```

Sin embargo, si un tipo de tupla variádica (`Vararg`) tiene variables libres, puede describir diferentes tipos de tuplas:

```jldoctest
julia> typeintersect(Tuple{Vararg{T} where T}, Tuple{Int,Float64})
Tuple{Int64, Float64}

julia> typeintersect(Tuple{Vararg{T}} where T, Tuple{Int,Float64})
Union{}
```

Tenga en cuenta que cuando `T` es libre con respecto al tipo `Tuple` (es decir, su tipo de unión `UnionAll` está fuera del tipo `Tuple`), solo un valor de `T` debe funcionar en todo el tipo. Por lo tanto, una tupla heterogénea no coincide.

Finalmente, vale la pena señalar que `Tuple{}` es distinto:

```jldoctest
julia> Tuple{}
Tuple{}

julia> Tuple{}.parameters
svec()

julia> typeintersect(Tuple{}, Tuple{Int})
Union{}
```

¿Qué es el tipo de tupla "primario"?

```julia-repl
julia> pointer_from_objref(Tuple)
Ptr{Cvoid} @0x00007f5998a04370

julia> pointer_from_objref(Tuple{})
Ptr{Cvoid} @0x00007f5998a570d0

julia> pointer_from_objref(Tuple.name.wrapper)
Ptr{Cvoid} @0x00007f5998a04370

julia> pointer_from_objref(Tuple{}.name.wrapper)
Ptr{Cvoid} @0x00007f5998a04370
```

así `Tuple == Tuple{Vararg{Any}}` es de hecho el tipo primario.

## Diagonal types

Considera el tipo `Tuple{T,T} where T`. Un método con esta firma se vería así:

```julia
f(x::T, y::T) where {T} = ...
```

Según la interpretación habitual de un tipo `UnionAll`, este `T` abarca todos los tipos, incluyendo `Any`, por lo que este tipo debería ser equivalente a `Tuple{Any,Any}`. Sin embargo, esta interpretación causa algunos problemas prácticos.

Primero, un valor de `T` necesita estar disponible dentro de la definición del método. Para una llamada como `f(1, 1.0)`, no está claro qué debería ser `T`. Podría ser `Union{Int,Float64}`, o quizás [`Real`](@ref). Intuitivamente, esperamos que la declaración `x::T` signifique `T === typeof(x)`. Para asegurarnos de que esa invariante se mantenga, necesitamos `typeof(x) === typeof(y) === T` en este método. Eso implica que el método solo debería ser llamado para argumentos del mismo tipo exacto.

Resulta que poder despachar si dos valores tienen el mismo tipo es muy útil (esto es utilizado por el sistema de promoción, por ejemplo), así que tenemos múltiples razones para querer una interpretación diferente de `Tuple{T,T} donde T`. Para hacer que esto funcione, añadimos la siguiente regla a la subtipificación: si una variable ocurre más de una vez en posición covariante, se restringe a abarcar solo tipos concretos. ("Posición covariante" significa que solo tipos `Tuple` y `Union` ocurren entre una ocurrencia de una variable y el tipo `UnionAll` que la introduce). Tales variables se llaman "variables diagonales" o "variables concretas".

Así que, por ejemplo, `Tuple{T,T} where T` puede verse como `Union{Tuple{Int8,Int8}, Tuple{Int16,Int16}, ...}`, donde `T` abarca todos los tipos concretos. Esto da lugar a algunos resultados interesantes de subtipado. Por ejemplo, `Tuple{Real,Real}` no es un subtipo de `Tuple{T,T} where T`, porque incluye algunos tipos como `Tuple{Int8,Int16}` donde los dos elementos tienen tipos diferentes. `Tuple{Real,Real}` y `Tuple{T,T} where T` tienen la intersección no trivial `Tuple{T,T} where T<:Real`. Sin embargo, `Tuple{Real}` *es* un subtipo de `Tuple{T} where T`, porque en ese caso `T` aparece solo una vez y, por lo tanto, no es diagonal.

A continuación, considera una firma como la siguiente:

```julia
f(a::Array{T}, x::T, y::T) where {T} = ...
```

En este caso, `T` ocurre en posición invariante dentro de `Array{T}`. Eso significa que cualquier tipo de arreglo que se pase determina de manera inequívoca el valor de `T` – decimos que `T` tiene una *restricción de igualdad* sobre él. Por lo tanto, en este caso, la regla diagonal no es realmente necesaria, ya que el arreglo determina `T` y luego podemos permitir que `x` e `y` sean de cualquier subtipo de `T`. Así que las variables que ocurren en posición invariante nunca se consideran diagonales. Esta elección de comportamiento es ligeramente controvertida – algunos sienten que esta definición debería escribirse como

```julia
f(a::Array{T}, x::S, y::S) where {T, S<:T} = ...
```

para aclarar si `x` e `y` necesitan tener el mismo tipo. En esta versión de la firma lo tendrían, o podríamos introducir una tercera variable para el tipo de `y` si `x` e `y` pueden tener tipos diferentes.

La siguiente complicación es la interacción de uniones y variables diagonales, por ejemplo.

```julia
f(x::Union{Nothing,T}, y::T) where {T} = ...
```

Considera lo que significa esta declaración. `y` tiene el tipo `T`. `x` puede tener el mismo tipo `T`, o bien ser del tipo [`Nothing`](@ref). Así que todas las siguientes llamadas deberían coincidir:

```julia
f(1, 1)
f("", "")
f(2.0, 2.0)
f(nothing, 1)
f(nothing, "")
f(nothing, 2.0)
```

Estos ejemplos nos están diciendo algo: cuando `x` es `nothing::Nothing`, no hay restricciones adicionales sobre `y`. Es como si la firma del método tuviera `y::Any`. De hecho, tenemos la siguiente equivalencia de tipos:

```julia
(Tuple{Union{Nothing,T},T} where T) == Union{Tuple{Nothing,Any}, Tuple{T,T} where T}
```

La regla general es: una variable concreta en posición covariante actúa como si no fuera concreta si el algoritmo de subtipado solo la *usa* una vez. Cuando `x` tiene tipo `Nothing`, no necesitamos usar el `T` en `Union{Nothing,T}`; solo lo usamos en la segunda posición. Esto surge naturalmente de la observación de que en `Tuple{T} donde T` restringir `T` a tipos concretos no hace ninguna diferencia; el tipo es igual a `Tuple{Any}` de cualquier manera.

Sin embargo, aparecer en una posición *invariante* descalifica a una variable de ser concreta, ya sea que esa aparición de la variable se use o no. De lo contrario, los tipos pueden comportarse de manera diferente dependiendo de qué otros tipos se comparen, haciendo que la subtipificación no sea transitiva. Por ejemplo, considera

```julia
Tuple{Int,Int8,Vector{Integer}} <: Tuple{T,T,Vector{Union{Integer,T}}} where T
```

Si se ignora el `T` dentro de la `Union`, entonces `T` es concreto y la respuesta es "falsa" ya que los dos primeros tipos no son iguales. Pero considera en su lugar

```julia
Tuple{Int,Int8,Vector{Any}} <: Tuple{T,T,Vector{Union{Integer,T}}} where T
```

Ahora no podemos ignorar el `T` en el `Union` (debemos tener `T == Any`), por lo que `T` no es concreto y la respuesta es "verdadero". Eso haría que la concreción de `T` dependiera del otro tipo, lo cual no es aceptable ya que un tipo debe tener un significado claro por sí mismo. Por lo tanto, la aparición de `T` dentro de `Vector` se considera en ambos casos.

## Subtyping diagonal variables

El algoritmo de subtipado para variables diagonales tiene dos componentes: (1) identificar las ocurrencias de variables, y (2) asegurar que las variables diagonales abarquen solo tipos concretos.

La primera tarea se logra manteniendo contadores `occurs_inv` y `occurs_cov` (en `src/subtype.c`) para cada variable en el entorno, rastreando el número de ocurrencias invariantes y covariantes, respectivamente. Una variable es diagonal cuando `occurs_inv == 0 && occurs_cov > 1`.

La segunda tarea se logra imponiendo una condición sobre el límite inferior de una variable. A medida que se ejecuta el algoritmo de subtipado, se estrechan los límites de cada variable (aumentando los límites inferiores y disminuyendo los límites superiores) para hacer un seguimiento del rango de valores de variable para los cuales se mantendría la relación de subtipo. Cuando terminamos de evaluar el cuerpo de un tipo `UnionAll` cuya variable es diagonal, observamos los valores finales de los límites. Dado que la variable debe ser concreta, ocurre una contradicción si su límite inferior no puede ser un subtipo de un tipo concreto. Por ejemplo, un tipo abstracto como [`AbstractArray`](@ref) no puede ser un subtipo de un tipo concreto, pero un tipo concreto como `Int` sí puede serlo, y el tipo vacío `Bottom` también puede serlo. Si un límite inferior no pasa esta prueba, el algoritmo se detiene con la respuesta `false`.

Por ejemplo, en el problema `Tuple{Int,String} <: Tuple{T,T} where T`, derivamos que esto sería cierto si `T` fuera un supertipo de `Union{Int,String}`. Sin embargo, `Union{Int,String}` es un tipo abstracto, por lo que la relación no se sostiene.

Esta prueba de concreción se realiza mediante la función `is_leaf_bound`. Tenga en cuenta que esta prueba es ligeramente diferente de `jl_is_leaf_type`, ya que también devuelve `true` para `Bottom`. Actualmente, esta función es heurística y no captura todos los posibles tipos concretos. La dificultad radica en que si un límite inferior es concreto puede depender de los valores de otros límites de variables de tipo. Por ejemplo, `Vector{T}` es equivalente al tipo concreto `Vector{Int}` solo si tanto los límites superiores como inferiores de `T` son iguales a `Int`. Aún no hemos desarrollado un algoritmo completo para esto.

## Introduction to the internal machinery

La mayoría de las operaciones para tratar con tipos se encuentran en los archivos `jltypes.c` y `subtype.c`. Una buena manera de comenzar es observar el subtipado en acción. Compila Julia con `make debug` y abre Julia dentro de un depurador. [gdb debugging tips](@ref gdb-debugging-tips) tiene algunos consejos que pueden ser útiles.

Debido a que el código de subtipo se utiliza mucho en el REPL mismo, y por lo tanto los puntos de interrupción en este código se activan con frecuencia, será más fácil si haces la siguiente definición:

```julia-repl
julia> function mysubtype(a,b)
           ccall(:jl_breakpoint, Cvoid, (Any,), nothing)
           a <: b
       end
```

y luego establece un punto de interrupción en `jl_breakpoint`. Una vez que se active este punto de interrupción, puedes establecer puntos de interrupción en otras funciones.

Como calentamiento, prueba lo siguiente:

```julia
mysubtype(Tuple{Int, Float64}, Tuple{Integer, Real})
```

Podemos hacerlo más interesante al intentar un caso más complejo:

```julia
mysubtype(Tuple{Array{Int,2}, Int8}, Tuple{Array{T}, T} where T)
```

## Subtyping and method sorting

Las funciones `type_morespecific` se utilizan para imponer un orden parcial en las funciones en las tablas de métodos (de más a menos específico). La especificidad es estricta; si `a` es más específico que `b`, entonces `a` no es igual a `b` y `b` no es más específico que `a`.

Si `a` es un subtipo estricto de `b`, entonces se considera automáticamente más específico. A partir de ahí, `type_morespecific` emplea algunas reglas menos formales. Por ejemplo, `subtype` es sensible al número de argumentos, pero `type_morespecific` puede no serlo. En particular, `Tuple{Int,AbstractFloat}` es más específico que `Tuple{Integer}`, aunque no sea un subtipo. (De `Tuple{Int,AbstractFloat}` y `Tuple{Integer,Float64}`, ninguno es más específico que el otro). Del mismo modo, `Tuple{Int,Vararg{Int}}` no es un subtipo de `Tuple{Integer}`, pero se considera más específico. Sin embargo, `morespecific` recibe un bono por longitud: en particular, `Tuple{Int,Int}` es más específico que `Tuple{Int,Vararg{Int}}`.

Si estás depurando cómo se ordenan los métodos, puede ser conveniente definir la función:

```julia
type_morespecific(a, b) = ccall(:jl_type_morespecific, Cint, (Any,Any), a, b)
```

que te permite probar si el tipo de tupla `a` es más específico que el tipo de tupla `b`.
