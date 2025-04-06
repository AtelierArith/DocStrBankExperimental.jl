# [Performance Tips](@id man-performance-tips)

En las siguientes secciones, revisaremos brevemente algunas técnicas que pueden ayudar a que tu código Julia se ejecute lo más rápido posible.

## Performance critical code should be inside a function

Cualquier código que sea crítico para el rendimiento debe estar dentro de una función. El código dentro de funciones tiende a ejecutarse mucho más rápido que el código de nivel superior, debido a cómo funciona el compilador de Julia.

El uso de funciones no solo es importante para el rendimiento: las funciones son más reutilizables y probables, y aclaran qué pasos se están realizando y cuáles son sus entradas y salidas, [Write functions, not just scripts](@ref) también es una recomendación de la Guía de Estilo de Julia.

Las funciones deben tomar argumentos, en lugar de operar directamente sobre variables globales, ver el siguiente punto.

## Avoid untyped global variables

El valor de una variable global no tipada puede cambiar en cualquier momento, lo que podría llevar a un cambio en su tipo. Esto dificulta que el compilador optimice el código que utiliza variables globales. Esto también se aplica a las variables con valor de tipo, es decir, alias de tipo a nivel global. Las variables deben ser locales o pasadas como argumentos a las funciones, siempre que sea posible.

Encontramos que los nombres globales son frecuentemente constantes, y declararlos como tales mejora significativamente el rendimiento:

```julia
const DEFAULT_VAL = 0
```

Si se sabe que un global siempre es del mismo tipo, [the type should be annotated](@ref man-typed-globals).

Los usos de variables globales no tipadas pueden ser optimizados al anotar sus tipos en el punto de uso:

```julia
global x = rand(1000)

function loop_over_global()
    s = 0.0
    for i in x::Vector{Float64}
        s += i
    end
    return s
end
```

Pasar argumentos a las funciones es un mejor estilo. Conduce a un código más reutilizable y aclara cuáles son las entradas y salidas.

!!! note
    Todo el código en el REPL se evalúa en el ámbito global, por lo que una variable definida y asignada en el nivel superior será una variable **global**. Las variables definidas en el ámbito de nivel superior dentro de los módulos también son globales.


En la siguiente sesión de REPL:

```julia-repl
julia> x = 1.0
```

es equivalente a:

```julia-repl
julia> global x = 1.0
```

así que todos los problemas de rendimiento discutidos anteriormente se aplican.

## Measure performance with [`@time`](@ref) and pay attention to memory allocation

Una herramienta útil para medir el rendimiento es el [`@time`](@ref) macro. Aquí repetimos el ejemplo con la variable global anterior, pero esta vez sin la anotación de tipo:

```jldoctest; setup = :(using Random; Random.seed!(1234)), filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(1000);

julia> function sum_global()
           s = 0.0
           for i in x
               s += i
           end
           return s
       end;

julia> @time sum_global()
  0.011539 seconds (9.08 k allocations: 373.386 KiB, 98.69% compilation time)
523.0007221951678

julia> @time sum_global()
  0.000091 seconds (3.49 k allocations: 70.156 KiB)
523.0007221951678
```

En la primera llamada (`@time sum_global()`) la función se compila. (Si aún no has utilizado [`@time`](@ref) en esta sesión, también se compilarán las funciones necesarias para el tiempo.) No deberías tomar en serio los resultados de esta ejecución. Para la segunda ejecución, ten en cuenta que además de informar el tiempo, también indicó que se había asignado una cantidad significativa de memoria. Aquí solo estamos calculando una suma sobre todos los elementos en un vector de flotantes de 64 bits, por lo que no debería ser necesario asignar memoria (en el montón).

Debemos aclarar que lo que `@time` informa son específicamente *asignaciones* de *heap*, que generalmente son necesarias para objetos mutables o para crear/aumentar contenedores de tamaño variable (como `Array` o `Dict`, cadenas, u objetos "inestables en tipo" cuyo tipo solo se conoce en tiempo de ejecución). Asignar (o desasignar) tales bloques de memoria puede requerir una llamada a función costosa a libc (por ejemplo, a través de `malloc` en C), y deben ser rastreados para la recolección de basura. En contraste, los valores inmutables como números (excepto bignums), tuplas y `struct`s inmutables se pueden almacenar de manera mucho más económica, por ejemplo, en memoria de pila o de registros de CPU, por lo que uno no suele preocuparse por el costo de rendimiento de "asignarlos".

La asignación de memoria inesperada es casi siempre un signo de algún problema con tu código, generalmente un problema de estabilidad de tipo o la creación de muchos arreglos temporales pequeños. En consecuencia, además de la asignación en sí, es muy probable que el código generado para tu función esté lejos de ser óptimo. Toma tales indicaciones en serio y sigue el consejo a continuación.

En este caso particular, la asignación de memoria se debe al uso de una variable global `x` inestable en cuanto al tipo, por lo que si en su lugar pasamos `x` como un argumento a la función, ya no se asigna memoria (la asignación restante reportada a continuación se debe a la ejecución del macro `@time` en el ámbito global) y es significativamente más rápida después de la primera llamada:

```jldoctest sumarg; setup = :(using Random; Random.seed!(1234)), filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(1000);

julia> function sum_arg(x)
           s = 0.0
           for i in x
               s += i
           end
           return s
       end;

julia> @time sum_arg(x)
  0.007551 seconds (3.98 k allocations: 200.548 KiB, 99.77% compilation time)
523.0007221951678

julia> @time sum_arg(x)
  0.000006 seconds (1 allocation: 16 bytes)
523.0007221951678
```

La 1 asignación vista proviene de ejecutar el macro `@time` en el ámbito global. Si en su lugar ejecutamos el tiempo en una función, podemos ver que, de hecho, no se realizan asignaciones:

```jldoctest sumarg; filter = r"[0-9\.]+ seconds"
julia> time_sum(x) = @time sum_arg(x);

julia> time_sum(x)
  0.000002 seconds
523.0007221951678
```

En algunas situaciones, su función puede necesitar asignar memoria como parte de su operación, y esto puede complicar la imagen simple anterior. En tales casos, considere usar uno de los [tools](@ref tools) a continuación para diagnosticar problemas, o escribir una versión de su función que separe la asignación de sus aspectos algorítmicos (ver [Pre-allocating outputs](@ref)).

!!! note
    Para un benchmarking más serio, considera el paquete [BenchmarkTools.jl](https://github.com/JuliaCI/BenchmarkTools.jl) que, entre otras cosas, evalúa la función múltiples veces para reducir el ruido.


## [Tools](@id tools)

Julia y su ecosistema de paquetes incluyen herramientas que pueden ayudarte a diagnosticar problemas y mejorar el rendimiento de tu código:

  * [Profiling](@ref) te permite medir el rendimiento de tu código en ejecución e identificar líneas que actúan como cuellos de botella. Para proyectos complejos, el paquete [ProfileView](https://github.com/timholy/ProfileView.jl) puede ayudarte a visualizar tus resultados de perfilado.
  * El paquete [JET](https://github.com/aviatesk/JET.jl) puede ayudarte a encontrar problemas de rendimiento comunes en tu código.
  * Asignaciones de memoria inesperadamente grandes, como las reportadas por [`@time`](@ref), [`@allocated`](@ref), o el perfilador (a través de llamadas a las rutinas de recolección de basura), sugieren que podría haber problemas con tu código. Si no ves otra razón para las asignaciones, sospecha de un problema de tipo. También puedes iniciar Julia con la opción `--track-allocation=user` y examinar los archivos resultantes `*.mem` para ver información sobre dónde ocurren esas asignaciones. Consulta [Memory allocation analysis](@ref).
  * `@code_warntype` generates a representation of your code that can be helpful in finding expressions that result in type uncertainty. See [`@code_warntype`](@ref) below.

## [Avoid containers with abstract type parameters](@id man-performance-abstract-container)

Al trabajar con tipos parametrizados, incluidos los arreglos, es mejor evitar parametrizar con tipos abstractos siempre que sea posible.

Por favor, proporciona el contenido en Markdown que deseas traducir al español.

```jldoctest
julia> a = Real[]
Real[]

julia> push!(a, 1); push!(a, 2.0); push!(a, π)
3-element Vector{Real}:
 1
 2.0
 π = 3.1415926535897...
```

Debido a que `a` es un arreglo de tipo abstracto [`Real`](@ref), debe ser capaz de contener cualquier valor `Real`. Dado que los objetos `Real` pueden ser de tamaño y estructura arbitrarios, `a` debe ser representado como un arreglo de punteros a objetos `Real` asignados individualmente. Sin embargo, si en su lugar solo permitimos almacenar números del mismo tipo, por ejemplo, [`Float64`](@ref), estos pueden ser almacenados de manera más eficiente:

```jldoctest
julia> a = Float64[]
Float64[]

julia> push!(a, 1); push!(a, 2.0); push!(a,  π)
3-element Vector{Float64}:
 1.0
 2.0
 3.141592653589793
```

Asignar números a `a` ahora los convertirá a `Float64` y `a` se almacenará como un bloque contiguo de valores de punto flotante de 64 bits que se pueden manipular de manera eficiente.

Si no puedes evitar contenedores con tipos de valor abstractos, a veces es mejor parametrizar con `Any` para evitar la verificación de tipos en tiempo de ejecución. Por ejemplo, `IdDict{Any, Any}` rinde mejor que `IdDict{Type, Vector}`.

Vea también la discusión bajo [Parametric Types](@ref).

## Type declarations

En muchos lenguajes con declaraciones de tipo opcionales, agregar declaraciones es la principal forma de hacer que el código se ejecute más rápido. Este *no* es el caso en Julia. En Julia, el compilador generalmente conoce los tipos de todos los argumentos de función, variables locales y expresiones. Sin embargo, hay algunas instancias específicas donde las declaraciones son útiles.

### Avoid fields with abstract type

Los tipos se pueden declarar sin especificar los tipos de sus campos:

```jldoctest myambig
julia> struct MyAmbiguousType
           a
       end
```

Esto permite que `a` sea de cualquier tipo. Esto puede ser útil a menudo, pero tiene una desventaja: para los objetos del tipo `MyAmbiguousType`, el compilador no podrá generar código de alto rendimiento. La razón es que el compilador utiliza los tipos de los objetos, no sus valores, para determinar cómo construir el código. Desafortunadamente, se puede inferir muy poco sobre un objeto del tipo `MyAmbiguousType`:

```jldoctest myambig
julia> b = MyAmbiguousType("Hello")
MyAmbiguousType("Hello")

julia> c = MyAmbiguousType(17)
MyAmbiguousType(17)

julia> typeof(b)
MyAmbiguousType

julia> typeof(c)
MyAmbiguousType
```

Los valores de `b` y `c` tienen el mismo tipo, sin embargo, su representación subyacente de datos en memoria es muy diferente. Incluso si solo almacenas valores numéricos en el campo `a`, el hecho de que la representación en memoria de un [`UInt8`](@ref) difiera de un [`Float64`](@ref) también significa que la CPU necesita manejarlos utilizando dos tipos diferentes de instrucciones. Dado que la información requerida no está disponible en el tipo, tales decisiones deben tomarse en tiempo de ejecución. Esto ralentiza el rendimiento.

Puedes hacerlo mejor declarando el tipo de `a`. Aquí, nos enfocamos en el caso en el que `a` podría ser cualquiera de varios tipos, en cuyo caso la solución natural es usar parámetros. Por ejemplo:

```jldoctest myambig2
julia> mutable struct MyType{T<:AbstractFloat}
           a::T
       end
```

Esta es una mejor opción que

```jldoctest myambig2
julia> mutable struct MyStillAmbiguousType
           a::AbstractFloat
       end
```

porque la primera versión especifica el tipo de `a` a partir del tipo del objeto envoltorio. Por ejemplo:

```jldoctest myambig2
julia> m = MyType(3.2)
MyType{Float64}(3.2)

julia> t = MyStillAmbiguousType(3.2)
MyStillAmbiguousType(3.2)

julia> typeof(m)
MyType{Float64}

julia> typeof(t)
MyStillAmbiguousType
```

El tipo del campo `a` se puede determinar fácilmente a partir del tipo de `m`, pero no a partir del tipo de `t`. De hecho, en `t` es posible cambiar el tipo del campo `a`:

```jldoctest myambig2
julia> typeof(t.a)
Float64

julia> t.a = 4.5f0
4.5f0

julia> typeof(t.a)
Float32
```

En contraste, una vez que `m` está construido, el tipo de `m.a` no puede cambiar:

```jldoctest myambig2
julia> m.a = 4.5f0
4.5f0

julia> typeof(m.a)
Float64
```

El hecho de que el tipo de `m.a` se conozca a partir del tipo de `m`—junto con el hecho de que su tipo no puede cambiar a mitad de la función—permite al compilador generar código altamente optimizado para objetos como `m`, pero no para objetos como `t`.

Por supuesto, todo esto es cierto solo si construimos `m` con un tipo concreto. Podemos romper esto construyéndolo explícitamente con un tipo abstracto:

```jldoctest myambig2
julia> m = MyType{AbstractFloat}(3.2)
MyType{AbstractFloat}(3.2)

julia> typeof(m.a)
Float64

julia> m.a = 4.5f0
4.5f0

julia> typeof(m.a)
Float32
```

Para todos los propósitos prácticos, tales objetos se comportan de manera idéntica a los de `MyStillAmbiguousType`.

Es bastante instructivo comparar la cantidad de código generado para una función simple.

```julia
func(m::MyType) = m.a+1
```

usando

```julia
code_llvm(func, Tuple{MyType{Float64}})
code_llvm(func, Tuple{MyType{AbstractFloat}})
```

Por razones de longitud, los resultados no se muestran aquí, pero es posible que desees intentarlo tú mismo. Debido a que el tipo está completamente especificado en el primer caso, el compilador no necesita generar ningún código para resolver el tipo en tiempo de ejecución. Esto resulta en un código más corto y rápido.

También se debe tener en cuenta que los tipos no completamente parametrizados se comportan como tipos abstractos. Por ejemplo, aunque un `Array{T,n}` completamente especificado es concreto, `Array` en sí, sin parámetros dados, no es concreto:

```jldoctest myambig3
julia> !isconcretetype(Array), !isabstracttype(Array), isstructtype(Array), !isconcretetype(Array{Int}), isconcretetype(Array{Int,1})
(true, true, true, true, true)
```

En este caso, sería mejor evitar declarar `MyType` con un campo `a::Array` y en su lugar declarar el campo como `a::Array{T,N}` o como `a::A`, donde `{T,N}` o `A` son parámetros de `MyType`.

El consejo anterior es especialmente útil cuando los campos de un struct están destinados a ser funciones, o más generalmente, objetos llamables. Es muy tentador definir un struct de la siguiente manera:

```julia
struct MyCallableWrapper
    f::Function
end
```

Pero dado que `Function` es un tipo abstracto, cada llamada a `wrapper.f` requerirá despacho dinámico, debido a la inestabilidad de tipo al acceder al campo `f`. En su lugar, deberías escribir algo como:

```julia
struct MyCallableWrapper{F}
    f::F
end
```

que tiene un comportamiento casi idéntico pero será mucho más rápido (porque se elimina la inestabilidad de tipo). Tenga en cuenta que no imponemos `F<:Function`: esto significa que los objetos llamables que no son subtipos de `Function` también están permitidos para el campo `f`.

### Avoid fields with abstract containers

Las mismas mejores prácticas también funcionan para los tipos de contenedores:

```jldoctest containers
julia> struct MySimpleContainer{A<:AbstractVector}
           a::A
       end

julia> struct MyAmbiguousContainer{T}
           a::AbstractVector{T}
       end

julia> struct MyAlsoAmbiguousContainer
           a::Array
       end
```

Por ejemplo:

```jldoctest containers
julia> c = MySimpleContainer(1:3);

julia> typeof(c)
MySimpleContainer{UnitRange{Int64}}

julia> c = MySimpleContainer([1:3;]);

julia> typeof(c)
MySimpleContainer{Vector{Int64}}

julia> b = MyAmbiguousContainer(1:3);

julia> typeof(b)
MyAmbiguousContainer{Int64}

julia> b = MyAmbiguousContainer([1:3;]);

julia> typeof(b)
MyAmbiguousContainer{Int64}

julia> d = MyAlsoAmbiguousContainer(1:3);

julia> typeof(d), typeof(d.a)
(MyAlsoAmbiguousContainer, Vector{Int64})

julia> d = MyAlsoAmbiguousContainer(1:1.0:3);

julia> typeof(d), typeof(d.a)
(MyAlsoAmbiguousContainer, Vector{Float64})

```

Para `MySimpleContainer`, el objeto está completamente especificado por su tipo y parámetros, por lo que el compilador puede generar funciones optimizadas. En la mayoría de los casos, esto probablemente será suficiente.

Mientras que el compilador ahora puede hacer su trabajo perfectamente, hay casos en los que *tú* podrías desear que tu código pudiera hacer cosas diferentes dependiendo del *tipo de elemento* de `a`. Por lo general, la mejor manera de lograr esto es envolver tu operación específica (aquí, `foo`) en una función separada:

```jldoctest containers
julia> function sumfoo(c::MySimpleContainer)
           s = 0
           for x in c.a
               s += foo(x)
           end
           s
       end
sumfoo (generic function with 1 method)

julia> foo(x::Integer) = x
foo (generic function with 1 method)

julia> foo(x::AbstractFloat) = round(x)
foo (generic function with 2 methods)
```

Esto mantiene las cosas simples, mientras permite que el compilador genere código optimizado en todos los casos.

Sin embargo, hay casos en los que puede que necesite declarar diferentes versiones de la función externa para diferentes tipos de elementos o tipos del `AbstractVector` del campo `a` en `MySimpleContainer`. Podría hacerlo de esta manera:

```jldoctest containers
julia> function myfunc(c::MySimpleContainer{<:AbstractArray{<:Integer}})
           return c.a[1]+1
       end
myfunc (generic function with 1 method)

julia> function myfunc(c::MySimpleContainer{<:AbstractArray{<:AbstractFloat}})
           return c.a[1]+2
       end
myfunc (generic function with 2 methods)

julia> function myfunc(c::MySimpleContainer{Vector{T}}) where T <: Integer
           return c.a[1]+3
       end
myfunc (generic function with 3 methods)
```

```jldoctest containers
julia> myfunc(MySimpleContainer(1:3))
2

julia> myfunc(MySimpleContainer(1.0:3))
3.0

julia> myfunc(MySimpleContainer([1:3;]))
4
```

### Annotate values taken from untyped locations

A menudo es conveniente trabajar con estructuras de datos que pueden contener valores de cualquier tipo (arreglos de tipo `Array{Any}`). Pero, si estás utilizando una de estas estructuras y sabes el tipo de un elemento, es útil compartir este conocimiento con el compilador:

```julia
function foo(a::Array{Any,1})
    x = a[1]::Int32
    b = x+1
    ...
end
```

Aquí, supimos que el primer elemento de `a` sería un [`Int32`](@ref). Hacer una anotación como esta tiene el beneficio adicional de que generará un error en tiempo de ejecución si el valor no es del tipo esperado, lo que podría detectar ciertos errores antes.

En el caso de que el tipo de `a[1]` no se conozca con precisión, `x` se puede declarar mediante `x = convert(Int32, a[1])::Int32`. El uso de la función [`convert`](@ref) permite que `a[1]` sea cualquier objeto convertible a un `Int32` (como `UInt8`), aumentando así la genericidad del código al aflojar el requisito de tipo. Observe que `convert` en sí mismo necesita una anotación de tipo en este contexto para lograr la estabilidad de tipo. Esto se debe a que el compilador no puede deducir el tipo del valor de retorno de una función, incluso `convert`, a menos que se conozcan los tipos de todos los argumentos de la función.

La anotación de tipo no mejorará (y puede, de hecho, obstaculizar) el rendimiento si el tipo es abstracto o se construye en tiempo de ejecución. Esto se debe a que el compilador no puede usar la anotación para especializar el código subsiguiente, y la verificación de tipo en sí misma toma tiempo. Por ejemplo, en el código:

```julia
function nr(a, prec)
    ctype = prec == 32 ? Float32 : Float64
    b = Complex{ctype}(a)
    c = (b + 1.0f0)::Complex{ctype}
    abs(c)
end
```

la anotación de `c` perjudica el rendimiento. Para escribir código eficiente que involucre tipos construidos en tiempo de ejecución, utiliza el [function-barrier technique](@ref kernel-functions) discutido a continuación, y asegúrate de que el tipo construido aparezca entre los tipos de argumento de la función del núcleo para que las operaciones del núcleo sean correctamente especializadas por el compilador. Por ejemplo, en el fragmento anterior, tan pronto como se construye `b`, se puede pasar a otra función `k`, el núcleo. Si, por ejemplo, la función `k` declara `b` como un argumento de tipo `Complex{T}`, donde `T` es un parámetro de tipo, entonces una anotación de tipo que aparezca en una declaración de asignación dentro de `k` de la forma:

```julia
c = (b + 1.0f0)::Complex{T}
```

no obstaculiza el rendimiento (pero tampoco ayuda) ya que el compilador puede determinar el tipo de `c` en el momento en que se compila `k`.

### Be aware of when Julia avoids specializing

Como heurística, Julia evita automáticamente [specializing](@ref man-method-specializations) en tres casos específicos de parámetros de tipo: `Type`, `Function` y `Vararg`. Julia siempre se especializará cuando el argumento se use dentro del método, pero no si el argumento solo se pasa a otra función. Esto generalmente no tiene impacto en el rendimiento en tiempo de ejecución y [improves compiler performance](@ref compiler-efficiency-issues). Si encuentras que sí tiene un impacto en el rendimiento en tiempo de ejecución en tu caso, puedes activar la especialización añadiendo un parámetro de tipo a la declaración del método. Aquí hay algunos ejemplos:

Esto no se especializará:

```julia
function f_type(t)  # or t::Type
    x = ones(t, 10)
    return sum(map(sin, x))
end
```

pero esto hará:

```julia
function g_type(t::Type{T}) where T
    x = ones(T, 10)
    return sum(map(sin, x))
end
```

Estos no se especializarán:

```julia
f_func(f, num) = ntuple(f, div(num, 2))
g_func(g::Function, num) = ntuple(g, div(num, 2))
```

pero esto hará:

```julia
h_func(h::H, num) where {H} = ntuple(h, div(num, 2))
```

Esto no se especializará:

```julia
f_vararg(x::Int...) = tuple(x...)
```

pero esto hará:

```julia
g_vararg(x::Vararg{Int, N}) where {N} = tuple(x...)
```

Solo se necesita introducir un único parámetro de tipo para forzar la especialización, incluso si los otros tipos no están restringidos. Por ejemplo, esto también especializará, y es útil cuando los argumentos no son todos del mismo tipo:

```julia
h_vararg(x::Vararg{Any, N}) where {N} = tuple(x...)
```

Tenga en cuenta que [`@code_typed`](@ref) y sus amigos siempre le mostrarán código especializado, incluso si Julia normalmente no especializaría esa llamada de método. Necesita verificar el [method internals](@ref ast-lowered-method) si desea ver si se generan especializaciones cuando se cambian los tipos de argumentos, es decir, si `Base.specializations(@which f(...))` contiene especializaciones para el argumento en cuestión.

## Break functions into multiple definitions

Escribir una función como muchas definiciones pequeñas permite al compilador llamar directamente al código más aplicable, o incluso incluirlo en línea.

Aquí hay un ejemplo de una "función compuesta" que realmente debería escribirse como múltiples definiciones:

```julia
using LinearAlgebra

function mynorm(A)
    if isa(A, Vector)
        return sqrt(real(dot(A,A)))
    elseif isa(A, Matrix)
        return maximum(svdvals(A))
    else
        error("mynorm: invalid argument")
    end
end
```

Esto se puede escribir de manera más concisa y eficiente como:

```julia
mynorm(x::Vector) = sqrt(real(dot(x, x)))
mynorm(A::Matrix) = maximum(svdvals(A))
```

Sin embargo, debe tenerse en cuenta que el compilador es bastante eficiente en la optimización de las ramas muertas en el código escrito como el ejemplo `mynorm`.

## Write "type-stable" functions

Cuando sea posible, ayuda a garantizar que una función siempre devuelva un valor del mismo tipo. Considera la siguiente definición:

```julia
pos(x) = x < 0 ? 0 : x
```

Aunque esto parece lo suficientemente inocente, el problema es que `0` es un entero (de tipo `Int`) y `x` podría ser de cualquier tipo. Por lo tanto, dependiendo del valor de `x`, esta función podría devolver un valor de cualquiera de los dos tipos. Este comportamiento es permitido y puede ser deseable en algunos casos. Pero se puede solucionar fácilmente de la siguiente manera:

```julia
pos(x) = x < 0 ? zero(x) : x
```

También hay una función [`oneunit`](@ref), y una función más general [`oftype(x, y)`](@ref), que devuelve `y` convertido al tipo de `x`.

## Avoid changing the type of a variable

Un problema análogo de "estabilidad de tipo" existe para las variables utilizadas repetidamente dentro de una función:

```julia
function foo()
    x = 1
    for i = 1:10
        x /= rand()
    end
    return x
end
```

La variable local `x` comienza como un entero, y después de una iteración del bucle se convierte en un número de punto flotante (el resultado del operador [`/`](@ref)). Esto dificulta que el compilador optimice el cuerpo del bucle. Hay varias soluciones posibles:

  * Inicializa `x` con `x = 1.0`
  * Declara el tipo de `x` explícitamente como `x::Float64 = 1`
  * Utiliza una conversión explícita mediante `x = oneunit(Float64)`
  * Inicializa con la primera iteración del bucle, a `x = 1 / rand()`, luego bucle `for i = 2:10`

## [Separate kernel functions (aka, function barriers)](@id kernel-functions)

Muchas funciones siguen un patrón de realizar un trabajo de configuración y luego ejecutar muchas iteraciones para realizar un cálculo central. Siempre que sea posible, es una buena idea colocar estos cálculos centrales en funciones separadas. Por ejemplo, la siguiente función inventada devuelve un array de un tipo elegido al azar:

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> function strange_twos(n)
           a = Vector{rand(Bool) ? Int64 : Float64}(undef, n)
           for i = 1:n
               a[i] = 2
           end
           return a
       end;

julia> strange_twos(3)
3-element Vector{Int64}:
 2
 2
 2
```

Esto debería escribirse como:

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> function fill_twos!(a)
           for i = eachindex(a)
               a[i] = 2
           end
       end;

julia> function strange_twos(n)
           a = Vector{rand(Bool) ? Int64 : Float64}(undef, n)
           fill_twos!(a)
           return a
       end;

julia> strange_twos(3)
3-element Vector{Int64}:
 2
 2
 2
```

El compilador de Julia especializa el código para los tipos de argumentos en los límites de las funciones, por lo que en la implementación original no conoce el tipo de `a` durante el bucle (ya que se elige aleatoriamente). Por lo tanto, la segunda versión es generalmente más rápida, ya que el bucle interno puede ser recompilado como parte de `fill_twos!` para diferentes tipos de `a`.

La segunda forma también suele ser un mejor estilo y puede llevar a una mayor reutilización del código.

Este patrón se utiliza en varios lugares de Julia Base. Por ejemplo, vea `vcat` y `hcat` en [`abstractarray.jl`](https://github.com/JuliaLang/julia/blob/40fe264f4ffaa29b749bcf42239a89abdcbba846/base/abstractarray.jl#L1205-L1206), o la función [`fill!`](@ref), que podríamos haber utilizado en lugar de escribir nuestra propia `fill_twos!`.

Funciones como `strange_twos` ocurren al tratar con datos de tipo incierto, por ejemplo, datos cargados desde un archivo de entrada que podrían contener enteros, flotantes, cadenas o algo más.

## [Types with values-as-parameters](@id man-performance-value-type)

Supongamos que quieres crear un array `N`-dimensional que tenga un tamaño de 3 a lo largo de cada eje. Tales arrays se pueden crear de esta manera:

```jldoctest
julia> A = fill(5.0, (3, 3))
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Este enfoque funciona muy bien: el compilador puede deducir que `A` es un `Array{Float64,2}` porque conoce el tipo del valor de relleno (`5.0::Float64`) y la dimensionalidad (`(3, 3)::NTuple{2,Int}`). Esto implica que el compilador puede generar un código muy eficiente para cualquier uso futuro de `A` en la misma función.

Pero ahora digamos que quieres escribir una función que crea un array de 3×3×... en dimensiones arbitrarias; podrías sentirte tentado a escribir una función

```jldoctest
julia> function array3(fillval, N)
           fill(fillval, ntuple(d->3, N))
       end
array3 (generic function with 1 method)

julia> array3(5.0, 2)
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Esto funciona, pero (como puedes verificar por ti mismo usando `@code_warntype array3(5.0, 2)`) el problema es que el tipo de salida no se puede inferir: el argumento `N` es un *valor* de tipo `Int`, y la inferencia de tipos no (y no puede) predecir su valor de antemano. Esto significa que el código que utiliza la salida de esta función tiene que ser conservador, verificando el tipo en cada acceso de `A`; dicho código será muy lento.

Ahora, una muy buena manera de resolver tales problemas es utilizando el [function-barrier technique](@ref kernel-functions). Sin embargo, en algunos casos, es posible que desees eliminar la inestabilidad de tipo por completo. En tales casos, un enfoque es pasar la dimensionalidad como un parámetro, por ejemplo a través de `Val{T}()` (ver ["Value types"](@ref)):

```jldoctest
julia> function array3(fillval, ::Val{N}) where N
           fill(fillval, ntuple(d->3, Val(N)))
       end
array3 (generic function with 1 method)

julia> array3(5.0, Val(2))
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Julia tiene una versión especializada de `ntuple` que acepta una instancia de `Val{::Int}` como segundo parámetro; al pasar `N` como un parámetro de tipo, haces que su "valor" sea conocido por el compilador. En consecuencia, esta versión de `array3` permite al compilador predecir el tipo de retorno.

Sin embargo, el uso de tales técnicas puede ser sorprendentemente sutil. Por ejemplo, no sería de ayuda si llamaras a `array3` desde una función como esta:

```julia
function call_array3(fillval, n)
    A = array3(fillval, Val(n))
end
```

Aquí, has creado el mismo problema una vez más: el compilador no puede adivinar qué es `n`, por lo que no sabe el *tipo* de `Val(n)`. Intentar usar `Val`, pero hacerlo incorrectamente, puede fácilmente empeorar el rendimiento en muchas situaciones. (Solo en situaciones donde efectivamente estás combinando `Val` con el truco de la barrera de función, para hacer que la función del núcleo sea más eficiente, debería usarse un código como el anterior.)

Un ejemplo de uso correcto de `Val` sería:

```julia
function filter3(A::AbstractArray{T,N}) where {T,N}
    kernel = array3(1, Val(N))
    filter(A, kernel)
end
```

En este ejemplo, `N` se pasa como un parámetro, por lo que su "valor" es conocido por el compilador. Esencialmente, `Val(T)` funciona solo cuando `T` es ya sea un valor codificado/ literal (`Val(3)`) o ya especificado en el dominio de tipos.

## The dangers of abusing multiple dispatch (aka, more on types with values-as-parameters)

Una vez que uno aprende a apreciar el despacho múltiple, hay una tendencia comprensible a exagerar y tratar de usarlo para todo. Por ejemplo, podrías imaginar usarlo para almacenar información, por ejemplo,

```
struct Car{Make, Model}
    year::Int
    ...more fields...
end
```

y luego despachar sobre objetos como `Car{:Honda,:Accord}(año, args...)`.

Esto podría valer la pena cuando se cumpla alguna de las siguientes condiciones:

  * Requiere un procesamiento intensivo de CPU en cada `Car`, y se vuelve mucho más eficiente si conoces la `Make` y el `Model` en tiempo de compilación y el número total de diferentes `Make` o `Model` que se utilizarán no es demasiado grande.
  * Tienes listas homogéneas del mismo tipo de `Car` para procesar, de modo que puedes almacenarlas todas en un `Array{Car{:Honda,:Accord},N}`.

Cuando esto último se cumple, una función que procesa un arreglo homogéneo puede ser especializada de manera productiva: Julia conoce el tipo de cada elemento de antemano (todos los objetos en el contenedor tienen el mismo tipo concreto), por lo que Julia puede "buscar" las llamadas a métodos correctas cuando la función se está compilando (eliminando la necesidad de verificar en tiempo de ejecución) y, por lo tanto, emitir código eficiente para procesar toda la lista.

Cuando estas condiciones no se cumplen, es probable que no obtengas ningún beneficio; peor aún, la "explosión combinatoria de tipos" resultante será contraproducente. Si `items[i+1]` tiene un tipo diferente al de `item[i]`, Julia tiene que buscar el tipo en tiempo de ejecución, buscar el método apropiado en las tablas de métodos, decidir (a través de la intersección de tipos) cuál coincide, determinar si ya ha sido compilado JIT (y hacerlo si no lo ha sido), y luego hacer la llamada. En esencia, estás pidiendo al sistema de tipos completo y a la maquinaria de compilación JIT que ejecute básicamente el equivalente de una declaración switch o una búsqueda en un diccionario en tu propio código.

Se pueden encontrar algunos benchmarks de tiempo de ejecución que comparan (1) la dispatch de tipo, (2) la búsqueda en diccionario y (3) una declaración "switch" en [on the mailing list](https://groups.google.com/forum/#!msg/julia-users/jUMu9A3QKQQ/qjgVWr7vAwAJ).

Quizás incluso peor que el impacto en tiempo de ejecución es el impacto en tiempo de compilación: Julia compilará funciones especializadas para cada diferente `Car{Make, Model}`; si tienes cientos o miles de tales tipos, entonces cada función que acepte tal objeto como parámetro (desde una función `get_year` personalizada que podrías escribir tú mismo, hasta la función genérica `push!` en Julia Base) tendrá cientos o miles de variantes compiladas para ella. Cada una de estas aumenta el tamaño de la caché de código compilado, la longitud de las listas internas de métodos, etc. Un entusiasmo excesivo por los valores como parámetros puede desperdiciar fácilmente enormes recursos.

## [Access arrays in memory order, along columns](@id man-performance-column-major)

Los arreglos multidimensionales en Julia se almacenan en orden por columnas. Esto significa que los arreglos se apilan una columna a la vez. Esto se puede verificar utilizando la función `vec` o la sintaxis `[:]` como se muestra a continuación (observe que el arreglo está ordenado como `[1 3 2 4]`, no como `[1 2 3 4]`):

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> x[:]
4-element Vector{Int64}:
 1
 3
 2
 4
```

Esta convención para ordenar arreglos es común en muchos lenguajes como Fortran, Matlab y R (por nombrar algunos). La alternativa al ordenamiento por columnas es el ordenamiento por filas, que es la convención adoptada por C y Python (`numpy`) entre otros lenguajes. Recordar el orden de los arreglos puede tener efectos significativos en el rendimiento al iterar sobre arreglos. Una regla general a tener en cuenta es que con arreglos por columnas, el primer índice cambia más rápidamente. Esencialmente, esto significa que la iteración será más rápida si el índice del bucle más interno es el primero en aparecer en una expresión de corte. Ten en cuenta que indexar un arreglo con `:` es un bucle implícito que accede iterativamente a todos los elementos dentro de una dimensión particular; puede ser más rápido extraer columnas que filas, por ejemplo.

Considere el siguiente ejemplo artificial. Imagina que queremos escribir una función que acepte un [`Vector`](@ref) y devuelva un cuadrado [`Matrix`](@ref) con las filas o las columnas llenas de copias del vector de entrada. Supongamos que no es importante si se llenan las filas o las columnas con estas copias (quizás el resto del código se pueda adaptar fácilmente en consecuencia). Podríamos hacer esto de al menos cuatro maneras (además de la llamada recomendada a la función incorporada [`repeat`](@ref)):

```julia
function copy_cols(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for i = inds
        out[:, i] = x
    end
    return out
end

function copy_rows(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for i = inds
        out[i, :] = x
    end
    return out
end

function copy_col_row(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for col = inds, row = inds
        out[row, col] = x[row]
    end
    return out
end

function copy_row_col(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for row = inds, col = inds
        out[row, col] = x[col]
    end
    return out
end
```

Ahora mediremos el tiempo de cada una de estas funciones utilizando el mismo vector de entrada aleatorio `10000` por `1`:

```julia-repl
julia> x = randn(10000);

julia> fmt(f) = println(rpad(string(f)*": ", 14, ' '), @elapsed f(x))

julia> map(fmt, [copy_cols, copy_rows, copy_col_row, copy_row_col]);
copy_cols:    0.331706323
copy_rows:    1.799009911
copy_col_row: 0.415630047
copy_row_col: 1.721531501
```

Observe que `copy_cols` es mucho más rápido que `copy_rows`. Esto es de esperar porque `copy_cols` respeta el diseño de memoria basado en columnas de la `Matrix` y lo llena una columna a la vez. Además, `copy_col_row` es mucho más rápido que `copy_row_col` porque sigue nuestra regla general de que el primer elemento que aparece en una expresión de corte debe estar acoplado con el bucle más interno.

## Pre-allocating outputs

Si tu función devuelve un `Array` o algún otro tipo complejo, puede que tenga que asignar memoria. Desafortunadamente, a menudo la asignación y su opuesto, la recolección de basura, son cuellos de botella sustanciales.

A veces puedes eludir la necesidad de asignar memoria en cada llamada a la función preasignando la salida. Como un ejemplo trivial, compara

```jldoctest prealloc
julia> function xinc(x)
           return [x, x+1, x+2]
       end;

julia> function loopinc()
           y = 0
           for i = 1:10^7
               ret = xinc(i)
               y += ret[2]
           end
           return y
       end;
```

con

```jldoctest prealloc
julia> function xinc!(ret::AbstractVector{T}, x::T) where T
           ret[1] = x
           ret[2] = x+1
           ret[3] = x+2
           nothing
       end;

julia> function loopinc_prealloc()
           ret = Vector{Int}(undef, 3)
           y = 0
           for i = 1:10^7
               xinc!(ret, i)
               y += ret[2]
           end
           return y
       end;
```

Resultados de tiempo:

```jldoctest prealloc; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> @time loopinc()
  0.529894 seconds (40.00 M allocations: 1.490 GiB, 12.14% gc time)
50000015000000

julia> @time loopinc_prealloc()
  0.030850 seconds (6 allocations: 288 bytes)
50000015000000
```

La preasignación tiene otras ventajas, por ejemplo, al permitir que el llamador controle el tipo de "salida" de un algoritmo. En el ejemplo anterior, podríamos haber pasado un `SubArray` en lugar de un [`Array`](@ref), si así lo hubiéramos deseado.

Llevado a su extremo, la preasignación puede hacer que tu código sea más feo, por lo que pueden ser necesarias mediciones de rendimiento y algo de juicio. Sin embargo, para funciones "vectorizadas" (elemento por elemento), se puede usar la sintaxis conveniente `x .= f.(y)` para operaciones en su lugar con bucles fusionados y sin arreglos temporales (ver el [dot syntax for vectorizing functions](@ref man-vectorized)).

## [Use `MutableArithmetics` for more control over allocation for mutable arithmetic types](@id man-perftips-mutablearithmetics)

Algunos [`Number`](@ref) subtipos, como [`BigInt`](@ref) o [`BigFloat`](@ref), pueden implementarse como tipos [`mutable struct`](@ref), o pueden tener componentes mutables. Las interfaces aritméticas en Julia `Base` generalmente optan por la conveniencia sobre la eficiencia en tales casos, por lo que usarlas de manera ingenua puede resultar en un rendimiento subóptimo. Las abstracciones del paquete [`MutableArithmetics`](https://juliahub.com/ui/Packages/General/MutableArithmetics), por otro lado, hacen posible aprovechar la mutabilidad de tales tipos para escribir código rápido que asigna solo lo necesario. `MutableArithmetics` también hace posible copiar valores de tipos aritméticos mutables explícitamente cuando es necesario. `MutableArithmetics` es un paquete de usuario y no está afiliado al proyecto Julia.

## More dots: Fuse vectorized operations

Julia tiene un [dot syntax](@ref man-vectorized) especial que convierte cualquier función escalar en una llamada a función "vectorizada", y cualquier operador en un operador "vectorizado", con la propiedad especial de que las "llamadas de punto" anidadas son *fusionadas*: se combinan a nivel de sintaxis en un solo bucle, sin asignar arreglos temporales. Si usas `.=` y operadores de asignación similares, el resultado también se puede almacenar en su lugar en un arreglo preasignado (ver arriba).

En un contexto de álgebra lineal, esto significa que, aunque operaciones como `vector + vector` y `vector * scalar` están definidas, puede ser ventajoso usar en su lugar `vector .+ vector` y `vector .* scalar` porque los bucles resultantes pueden fusionarse con los cálculos circundantes. Por ejemplo, considere las dos funciones:

```jldoctest dotfuse
julia> f(x) = 3x.^2 + 4x + 7x.^3;

julia> fdot(x) = @. 3x^2 + 4x + 7x^3; # equivalent to 3 .* x.^2 .+ 4 .* x .+ 7 .* x.^3
```

Ambos `f` y `fdot` calculan lo mismo. Sin embargo, `fdot` (definido con la ayuda del macro [`@.`](@ref @__dot__)) es significativamente más rápido cuando se aplica a un array:

```jldoctest dotfuse; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(10^6);

julia> @time f(x);
  0.019049 seconds (16 allocations: 45.777 MiB, 18.59% gc time)

julia> @time fdot(x);
  0.002790 seconds (6 allocations: 7.630 MiB)

julia> @time f.(x);
  0.002626 seconds (8 allocations: 7.630 MiB)
```

Es decir, `fdot(x)` es diez veces más rápido y asigna 1/6 de la memoria de `f(x)`, porque cada operación de `*` y `+` en `f(x)` asigna un nuevo arreglo temporal y se ejecuta en un bucle separado. En este ejemplo, `f.(x)` es tan rápido como `fdot(x)`, pero en muchos contextos es más conveniente esparcir algunos puntos en tus expresiones que definir una función separada para cada operación vectorizada.

## [Fewer dots: Unfuse certain intermediate broadcasts](@id man-performance-unfuse)

La fusión de bucles de punto mencionada anteriormente permite un código conciso e idiomático para expresar operaciones de alto rendimiento. Sin embargo, es importante recordar que la operación fusionada se calculará en cada iteración de la transmisión. Esto significa que en algunas situaciones, particularmente en presencia de transmisiones compuestas o multidimensionales, una expresión con llamadas de punto puede estar calculando una función más veces de lo previsto. Como ejemplo, digamos que queremos construir una matriz aleatoria cuyas filas tengan norma euclidiana uno. Podríamos escribir algo como lo siguiente:

```
julia> x = rand(1000, 1000);

julia> d = sum(abs2, x; dims=2);

julia> @time x ./= sqrt.(d);
  0.002049 seconds (4 allocations: 96 bytes)
```

Esto funcionará. Sin embargo, esta expresión en realidad volverá a calcular `sqrt(d[i])` para *cada* elemento en la fila `x[i, :]`, lo que significa que se calcularán muchas más raíces cuadradas de las necesarias. Para ver precisamente sobre qué índices iterará la difusión, podemos llamar a `Broadcast.combine_axes` sobre los argumentos de la expresión fusionada. Esto devolverá una tupla de rangos cuyos elementos corresponden a los ejes de iteración; el producto de las longitudes de estos rangos será el número total de llamadas a la operación fusionada.

Se sigue que cuando algunos componentes de la expresión de difusión son constantes a lo largo de un eje—como el `sqrt` a lo largo de la segunda dimensión en el ejemplo anterior—hay potencial para una mejora en el rendimiento al "desfusionar" forzosamente esos componentes, es decir, asignar el resultado de la operación de difusión por adelantado y reutilizar el valor en caché a lo largo de su eje constante. Algunos enfoques potenciales son usar variables temporales, envolver componentes de una expresión de punto en `identity`, o usar una función intrínsecamente vectorizada equivalente (pero no fusionada).

```
julia> @time let s = sqrt.(d); x ./= s end;
  0.000809 seconds (5 allocations: 8.031 KiB)

julia> @time x ./= identity(sqrt.(d));
  0.000608 seconds (5 allocations: 8.031 KiB)

julia> @time x ./= map(sqrt, d);
  0.000611 seconds (4 allocations: 8.016 KiB)
```

Cualquiera de estas opciones produce aproximadamente un aumento de velocidad de tres veces a costa de una asignación; para broadcastables grandes, este aumento de velocidad puede ser asintóticamente muy grande.

## [Consider using views for slices](@id man-performance-views)

En Julia, una expresión de "slice" de un array como `array[1:5, :]` crea una copia de esos datos (excepto en el lado izquierdo de una asignación, donde `array[1:5, :] = ...` asigna en su lugar a esa porción de `array`). Si estás realizando muchas operaciones en el slice, esto puede ser bueno para el rendimiento porque es más eficiente trabajar con una copia contigua más pequeña que indexar en el array original. Por otro lado, si solo estás realizando unas pocas operaciones simples en el slice, el costo de las operaciones de asignación y copia puede ser sustancial.

Una alternativa es crear una "vista" del arreglo, que es un objeto de arreglo (un `SubArray`) que en realidad hace referencia a los datos del arreglo original en su lugar, sin hacer una copia. (Si escribes en una vista, también modifica los datos del arreglo original). Esto se puede hacer para rebanadas individuales llamando a [`view`](@ref), o más simplemente para toda una expresión o bloque de código poniendo [`@views`](@ref) delante de esa expresión. Por ejemplo:

```jldoctest; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> fcopy(x) = sum(x[2:end-1]);

julia> @views fview(x) = sum(x[2:end-1]);

julia> x = rand(10^6);

julia> @time fcopy(x);
  0.003051 seconds (3 allocations: 7.629 MB)

julia> @time fview(x);
  0.001020 seconds (1 allocation: 16 bytes)
```

Nota tanto la aceleración de 3× como la disminución de la asignación de memoria de la versión `fview` de la función.

## Copying data is not always bad

Los arreglos se almacenan de manera contigua en la memoria, lo que favorece la vectorización de la CPU y reduce los accesos a la memoria debido a la caché. Estas son las mismas razones por las que se recomienda acceder a los arreglos en orden de columna (ver arriba). Los patrones de acceso irregulares y las vistas no contiguas pueden ralentizar drásticamente los cálculos en los arreglos debido al acceso no secuencial a la memoria.

Copiar datos de acceso irregular en un arreglo contiguo antes de acceder a ellos repetidamente puede resultar en una gran aceleración, como en el ejemplo a continuación. Aquí, se accede a una matriz en índices aleatoriamente mezclados antes de ser multiplicada. Copiar en arreglos simples acelera la multiplicación incluso con el costo adicional de la copia y la asignación.

```julia-repl
julia> using Random

julia> A = randn(3000, 3000);

julia> x = randn(2000);

julia> inds = shuffle(1:3000)[1:2000];

julia> function iterated_neural_network(A, x, depth)
           for _ in 1:depth
               x .= max.(0, A * x)
           end
           argmax(x)
       end

julia> @time iterated_neural_network(view(A, inds, inds), x, 10)
  0.324903 seconds (12 allocations: 157.562 KiB)
1569

julia> @time iterated_neural_network(A[inds, inds], x, 10)
  0.054576 seconds (13 allocations: 30.671 MiB, 13.33% gc time)
1569
```

Siempre que haya suficiente memoria, el costo de copiar la vista a un arreglo se ve superado por el aumento de velocidad al realizar las multiplicaciones de matrices repetidas en un arreglo contiguo.

## Consider StaticArrays.jl for small fixed-size vector/matrix operations

Si tu aplicación implica muchos arreglos pequeños (`< 100` elementos) de tamaños fijos (es decir, el tamaño se conoce antes de la ejecución), entonces podrías considerar usar el [StaticArrays.jl package](https://github.com/JuliaArrays/StaticArrays.jl). Este paquete te permite representar tales arreglos de una manera que evita asignaciones innecesarias en el heap y permite que el compilador especialice el código para el *tamaño* del arreglo, por ejemplo, desenrollando completamente las operaciones vectoriales (eliminando los bucles) y almacenando elementos en registros de la CPU.

Por ejemplo, si estás realizando cálculos con geometrías en 2D, podrías tener muchos cálculos con vectores de 2 componentes. Al usar el tipo `SVector` de StaticArrays.jl, puedes utilizar una notación y operaciones de vectores convenientes como `norm(3v - w)` en los vectores `v` y `w`, permitiendo que el compilador desarrolle el código a un cálculo mínimo equivalente a `@inbounds hypot(3v[1]-w[1], 3v[2]-w[2])`.

## Avoid string interpolation for I/O

Al escribir datos en un archivo (o en otro dispositivo de E/S), formar cadenas intermedias adicionales es una fuente de sobrecarga. En lugar de:

```julia
println(file, "$a $b")
```

usar:

```julia
println(file, a, " ", b)
```

La primera versión del código forma una cadena, luego la escribe en el archivo, mientras que la segunda versión escribe valores directamente en el archivo. También nota que en algunos casos la interpolación de cadenas puede ser más difícil de leer. Considera:

```julia
println(file, "$(f(a))$(f(b))")
```

versus:

```julia
println(file, f(a), f(b))
```

## Optimize network I/O during parallel execution

Al ejecutar una función remota en paralelo:

```julia
using Distributed

responses = Vector{Any}(undef, nworkers())
@sync begin
    for (idx, pid) in enumerate(workers())
        @async responses[idx] = remotecall_fetch(foo, pid, args...)
    end
end
```

es más rápido que:

```julia
using Distributed

refs = Vector{Any}(undef, nworkers())
for (idx, pid) in enumerate(workers())
    refs[idx] = @spawnat pid foo(args...)
end
responses = [fetch(r) for r in refs]
```

El primero resulta en un solo viaje de red a cada trabajador, mientras que el segundo resulta en dos llamadas de red: primero por el [`@spawnat`](@ref) y el segundo debido al [`fetch`](@ref) (o incluso un [`wait`](@ref)). El `4d61726b646f776e2e436f64652822222c202266657463682229_40726566`/`4d61726b646f776e2e436f64652822222c2022776169742229_40726566` también se está ejecutando de manera serial, lo que resulta en un rendimiento general más pobre.

## Fix deprecation warnings

Una función obsoleta realiza internamente una búsqueda para imprimir una advertencia relevante solo una vez. Esta búsqueda adicional puede causar una desaceleración significativa, por lo que todos los usos de funciones obsoletas deben ser modificados como se sugiere en las advertencias.

## Tweaks

Estos son algunos puntos menores que podrían ayudar en bucles internos ajustados.

  * Evita arreglos innecesarios. Por ejemplo, en lugar de [`sum([x,y,z])`](@ref), usa `x+y+z`.
  * Utiliza [`abs2(z)`](@ref) en lugar de [`abs(z)^2`](@ref) para `z` complejo. En general, intenta reescribir el código para usar [`abs2`](@ref) en lugar de [`abs`](@ref) para argumentos complejos.
  * Utiliza [`div(x,y)`](@ref) para la división truncada de enteros en lugar de [`trunc(x/y)`](@ref), [`fld(x,y)`](@ref) en lugar de [`floor(x/y)`](@ref), y [`cld(x,y)`](@ref) en lugar de [`ceil(x/y)`](@ref).

## [Performance Annotations](@id man-performance-annotations)

A veces puedes habilitar una mejor optimización al prometer ciertas propiedades del programa.

  * Utiliza [`@inbounds`](@ref) para eliminar la verificación de límites de matriz dentro de las expresiones. Asegúrate antes de hacer esto. Si los índices están fuera de los límites, puedes sufrir bloqueos o corrupción silenciosa.
  * Utilice [`@fastmath`](@ref) para permitir optimizaciones de punto flotante que son correctas para números reales, pero que conducen a diferencias para números IEEE. Tenga cuidado al hacer esto, ya que puede cambiar los resultados numéricos. Esto corresponde a la opción `-ffast-math` de clang.
  * Escribe [`@simd`](@ref) frente a los bucles `for` para prometer que las iteraciones son independientes y pueden ser reordenadas. Ten en cuenta que en muchos casos, Julia puede vectorizar automáticamente el código sin el macro `@simd`; solo es beneficioso en casos donde tal transformación sería de otro modo ilegal, incluidos casos como permitir la re-asociatividad de punto flotante e ignorar accesos a memoria dependientes (`@simd ivdep`). Nuevamente, ten mucho cuidado al afirmar `@simd`, ya que anotar erróneamente un bucle con iteraciones dependientes puede resultar en resultados inesperados. En particular, ten en cuenta que `setindex!` en algunos subtipos de `AbstractArray` es inherentemente dependiente del orden de iteración. **Esta característica es experimental** y podría cambiar o desaparecer en futuras versiones de Julia.

El uso del modismo común de utilizar 1:n para indexar en un AbstractArray no es seguro si el Array utiliza indexación no convencional, y puede causar un fallo de segmentación si la verificación de límites está desactivada. Utiliza `LinearIndices(x)` o `eachindex(x)` en su lugar (ver también [Arrays with custom indices](@ref man-custom-indices)).

!!! note
    Mientras que `@simd` debe colocarse directamente frente a un bucle `for` más interno, tanto `@inbounds` como `@fastmath` se pueden aplicar a expresiones individuales o a todas las expresiones que aparecen dentro de bloques de código anidados, por ejemplo, usando `@inbounds begin` o `@inbounds for ...`.


Aquí hay un ejemplo con las marcas `@inbounds` y `@simd` (aquí usamos `@noinline` para evitar que el optimizador intente ser demasiado astuto y derrote nuestra evaluación):

```julia
@noinline function inner(x, y)
    s = zero(eltype(x))
    for i=eachindex(x)
        @inbounds s += x[i]*y[i]
    end
    return s
end

@noinline function innersimd(x, y)
    s = zero(eltype(x))
    @simd for i = eachindex(x)
        @inbounds s += x[i] * y[i]
    end
    return s
end

function timeit(n, reps)
    x = rand(Float32, n)
    y = rand(Float32, n)
    s = zero(Float64)
    time = @elapsed for j in 1:reps
        s += inner(x, y)
    end
    println("GFlop/sec        = ", 2n*reps / time*1E-9)
    time = @elapsed for j in 1:reps
        s += innersimd(x, y)
    end
    println("GFlop/sec (SIMD) = ", 2n*reps / time*1E-9)
end

timeit(1000, 1000)
```

En una computadora con un procesador Intel Core i5 de 2.4GHz, esto produce:

```
GFlop/sec        = 1.9467069505224963
GFlop/sec (SIMD) = 17.578554163920018
```

(`GFlop/sec` mide el rendimiento, y números más grandes son mejores.)

Aquí hay un ejemplo con los tres tipos de marcado. Este programa primero calcula la diferencia finita de un arreglo unidimensional y luego evalúa la norma L2 del resultado:

```julia
function init!(u::Vector)
    n = length(u)
    dx = 1.0 / (n-1)
    @fastmath @inbounds @simd for i in 1:n #by asserting that `u` is a `Vector` we can assume it has 1-based indexing
        u[i] = sin(2pi*dx*i)
    end
end

function deriv!(u::Vector, du)
    n = length(u)
    dx = 1.0 / (n-1)
    @fastmath @inbounds du[1] = (u[2] - u[1]) / dx
    @fastmath @inbounds @simd for i in 2:n-1
        du[i] = (u[i+1] - u[i-1]) / (2*dx)
    end
    @fastmath @inbounds du[n] = (u[n] - u[n-1]) / dx
end

function mynorm(u::Vector)
    n = length(u)
    T = eltype(u)
    s = zero(T)
    @fastmath @inbounds @simd for i in 1:n
        s += u[i]^2
    end
    @fastmath @inbounds return sqrt(s)
end

function main()
    n = 2000
    u = Vector{Float64}(undef, n)
    init!(u)
    du = similar(u)

    deriv!(u, du)
    nu = mynorm(du)

    @time for i in 1:10^6
        deriv!(u, du)
        nu = mynorm(du)
    end

    println(nu)
end

main()
```

En una computadora con un procesador Intel Core i7 de 2.7 GHz, esto produce:

```
$ julia wave.jl;
  1.207814709 seconds
4.443986180758249

$ julia --math-mode=ieee wave.jl;
  4.487083643 seconds
4.443986180758249
```

Aquí, la opción `--math-mode=ieee` desactiva el macro `@fastmath`, para que podamos comparar resultados.

En este caso, la aceleración debido a `@fastmath` es un factor de aproximadamente 3.7. Esto es inusualmente grande; en general, la aceleración será menor. (En este ejemplo particular, el conjunto de trabajo del benchmark es lo suficientemente pequeño como para caber en la caché L1 del procesador, de modo que la latencia de acceso a la memoria no juega un papel, y el tiempo de computación está dominado por el uso de la CPU. En muchos programas del mundo real, este no es el caso). Además, en este caso, esta optimización no cambia el resultado; en general, el resultado será ligeramente diferente. En algunos casos, especialmente para algoritmos numéricamente inestables, el resultado puede ser muy diferente.

La anotación `@fastmath` reorganiza las expresiones de punto flotante, por ejemplo, cambiando el orden de evaluación o asumiendo que ciertos casos especiales (inf, nan) no pueden ocurrir. En este caso (y en esta computadora en particular), la principal diferencia es que la expresión `1 / (2*dx)` en la función `deriv` se eleva fuera del bucle (es decir, se calcula fuera del bucle), como si se hubiera escrito `idx = 1 / (2*dx)`. En el bucle, la expresión `... / (2*dx)` se convierte entonces en `... * idx`, lo que es mucho más rápido de evaluar. Por supuesto, tanto la optimización real que aplica el compilador como la aceleración resultante dependen mucho del hardware. Puedes examinar el cambio en el código generado utilizando la función [`code_native`](@ref) de Julia.

Tenga en cuenta que `@fastmath` también asume que no ocurrirán `NaN`s durante el cálculo, lo que puede llevar a un comportamiento sorprendente:

```julia-repl
julia> f(x) = isnan(x);

julia> f(NaN)
true

julia> f_fast(x) = @fastmath isnan(x);

julia> f_fast(NaN)
false
```

## Treat Subnormal Numbers as Zeros

Los números subnormales, anteriormente llamados [denormal numbers](https://en.wikipedia.org/wiki/Denormal_number), son útiles en muchos contextos, pero incurren en una penalización de rendimiento en algunos hardware. Una llamada [`set_zero_subnormals(true)`](@ref) otorga permiso para que las operaciones de punto flotante traten las entradas o salidas subnormales como ceros, lo que puede mejorar el rendimiento en algunos hardware. Una llamada [`set_zero_subnormals(false)`](@ref) impone un comportamiento estricto de IEEE para los números subnormales.

A continuación se muestra un ejemplo donde los subnormales impactan notablemente en el rendimiento de cierto hardware:

```julia
function timestep(b::Vector{T}, a::Vector{T}, Δt::T) where T
    @assert length(a)==length(b)
    n = length(b)
    b[1] = 1                            # Boundary condition
    for i=2:n-1
        b[i] = a[i] + (a[i-1] - T(2)*a[i] + a[i+1]) * Δt
    end
    b[n] = 0                            # Boundary condition
end

function heatflow(a::Vector{T}, nstep::Integer) where T
    b = similar(a)
    for t=1:div(nstep,2)                # Assume nstep is even
        timestep(b,a,T(0.1))
        timestep(a,b,T(0.1))
    end
end

heatflow(zeros(Float32,10),2)           # Force compilation
for trial=1:6
    a = zeros(Float32,1000)
    set_zero_subnormals(iseven(trial))  # Odd trials use strict IEEE arithmetic
    @time heatflow(a,1000)
end
```

Esto da una salida similar a

```
  0.002202 seconds (1 allocation: 4.063 KiB)
  0.001502 seconds (1 allocation: 4.063 KiB)
  0.002139 seconds (1 allocation: 4.063 KiB)
  0.001454 seconds (1 allocation: 4.063 KiB)
  0.002115 seconds (1 allocation: 4.063 KiB)
  0.001455 seconds (1 allocation: 4.063 KiB)
```

Nota cómo cada iteración par es significativamente más rápida.

Este ejemplo genera muchos números subnormales porque los valores en `a` se convierten en una curva que disminuye exponencialmente, la cual se aplana lentamente con el tiempo.

Tratar los subnormales como ceros debe hacerse con precaución, porque hacerlo rompe algunas identidades, como `x-y == 0` implica `x == y`:

```jldoctest
julia> x = 3f-38; y = 2f-38;

julia> set_zero_subnormals(true); (x - y, x == y)
(0.0f0, false)

julia> set_zero_subnormals(false); (x - y, x == y)
(1.0000001f-38, false)
```

En algunas aplicaciones, una alternativa a poner en cero los números subnormales es inyectar un pequeño bit de ruido. Por ejemplo, en lugar de inicializar `a` con ceros, inicialízalo con:

```julia
a = rand(Float32,1000) * 1.f-9
```

## [[`@code_warntype`](@ref)](@id man-code-warntype)

El macro [`@code_warntype`](@ref) (o su variante de función [`code_warntype`](@ref)) puede ser útil a veces para diagnosticar problemas relacionados con tipos. Aquí hay un ejemplo:

```julia-repl
julia> @noinline pos(x) = x < 0 ? 0 : x;

julia> function f(x)
           y = pos(x)
           return sin(y*x + 1)
       end;

julia> @code_warntype f(3.2)
MethodInstance for f(::Float64)
  from f(x) @ Main REPL[9]:1
Arguments
  #self#::Core.Const(f)
  x::Float64
Locals
  y::Union{Float64, Int64}
Body::Float64
1 ─      (y = Main.pos(x))
│   %2 = (y * x)::Float64
│   %3 = (%2 + 1)::Float64
│   %4 = Main.sin(%3)::Float64
└──      return %4
```

Interpretar la salida de [`@code_warntype`](@ref), al igual que la de sus primos [`@code_lowered`](@ref), [`@code_typed`](@ref), [`@code_llvm`](@ref), y [`@code_native`](@ref), requiere un poco de práctica. Tu código se presenta en una forma que ha sido digerida en gran medida en su camino hacia la generación de código de máquina compilado. La mayoría de las expresiones están anotadas por un tipo, indicado por `::T` (donde `T` podría ser [`Float64`](@ref), por ejemplo). La característica más importante de `4d61726b646f776e2e436f64652822222c202240636f64655f7761726e747970652229_40726566` es que los tipos no concretos se muestran en ROJO; dado que este documento está escrito en Markdown, que no tiene color, en este documento, el texto ROJO se denota en mayúsculas.

En la parte superior, el tipo de retorno inferido de la función se muestra como `Body::Float64`. Las siguientes líneas representan el cuerpo de `f` en la forma IR SSA de Julia. Las cajas numeradas son etiquetas y representan objetivos para saltos (a través de `goto`) en tu código. Al observar el cuerpo, puedes ver que lo primero que sucede es que se llama a `pos` y el valor de retorno ha sido inferido como el tipo `Union` `Union{Float64, Int64}` mostrado en mayúsculas ya que es un tipo no concreto. Esto significa que no podemos conocer el tipo de retorno exacto de `pos` basado en los tipos de entrada. Sin embargo, el resultado de `y*x` es un `Float64` sin importar si `y` es un `Float64` o `Int64`. El resultado neto es que `f(x::Float64)` no será inestable en su salida, incluso si algunos de los cálculos intermedios son inestables en cuanto a tipos.

Cómo uses esta información depende de ti. Obviamente, sería lo mejor fijar `pos` para que sea de tipo estable: si lo hicieras, todas las variables en `f` serían concretas y su rendimiento sería óptimo. Sin embargo, hay circunstancias en las que este tipo de inestabilidad de tipo *efímera* podría no importar demasiado: por ejemplo, si `pos` nunca se usa de forma aislada, el hecho de que la salida de `f` sea de tipo estable (para entradas [`Float64`](@ref)) protegerá el código posterior de los efectos propagadores de la inestabilidad de tipo. Esto es particularmente relevante en casos donde fijar la inestabilidad de tipo es difícil o imposible. En tales casos, los consejos anteriores (por ejemplo, agregar anotaciones de tipo y/o dividir funciones) son tus mejores herramientas para contener el "daño" de la inestabilidad de tipo. Además, ten en cuenta que incluso Julia Base tiene funciones que son inestables en cuanto a tipo. Por ejemplo, la función [`findfirst`](@ref) devuelve el índice en un array donde se encuentra una clave, o `nothing` si no se encuentra, una clara inestabilidad de tipo. Para facilitar la identificación de las inestabilidades de tipo que probablemente sean importantes, los `Union` que contienen `missing` o `nothing` se resaltan en amarillo, en lugar de rojo.

Los siguientes ejemplos pueden ayudarte a interpretar expresiones marcadas como que contienen tipos no hoja:

  * Cuerpo de la función que comienza con `Body::Union{T1,T2})`

      * Interpretación: función con tipo de retorno inestable
      * Sugerencia: haz que el tipo de valor de retorno sea estable, incluso si tienes que anotarlo.
  * `invocar Main.g(%%x::Int64)::Unión{Float64, Int64}`

      * Interpretación: llamada a una función `g` inestable en tipo.
      * Sugerencia: arreglar la función, o si es necesario, anotar el valor de retorno.
  * `invocar Base.getindex(%%x::Array{Any,1}, 1::Int64)::Any`

      * Interpretación: acceso a elementos de arreglos mal tipados
      * Sugerencia: utiliza arreglos con tipos mejor definidos, o si es necesario, anota el tipo de accesos a elementos individuales.
  * `Base.getfield(%%x, :(:data))::Array{Float64,N} donde N`

      * Interpretación: obtener un campo que no es de tipo hoja. En este caso, el tipo de `x`, digamos `ArrayContainer`, tenía un campo `data::Array{T}`. Pero `Array` también necesita la dimensión `N` para ser un tipo concreto.
      * Sugerencia: utiliza tipos concretos como `Array{T,3}` o `Array{T,N}`, donde `N` es ahora un parámetro de `ArrayContainer`

## [Performance of captured variable](@id man-performance-captured)

Considere el siguiente ejemplo que define una función interna:

```julia
function abmult(r::Int)
    if r < 0
        r = -r
    end
    f = x -> x * r
    return f
end
```

La función `abmult` devuelve una función `f` que multiplica su argumento por el valor absoluto de `r`. La función interna asignada a `f` se llama "cerradura". Las funciones internas también son utilizadas por el lenguaje para bloques `do` y para expresiones generadoras.

Este estilo de código presenta desafíos de rendimiento para el lenguaje. El analizador, al traducirlo a instrucciones de nivel inferior, reorganiza sustancialmente el código anterior extrayendo la función interna a un bloque de código separado. Las variables "capturadas" como `r` que son compartidas por funciones internas y su ámbito envolvente también se extraen en una "caja" asignada en el montón accesible tanto para funciones internas como externas, porque el lenguaje especifica que `r` en el ámbito interno debe ser idéntico a `r` en el ámbito externo incluso después de que el ámbito externo (u otra función interna) modifique `r`.

La discusión en el párrafo anterior se refería al "analizador", es decir, la fase de compilación que tiene lugar cuando el módulo que contiene `abmult` se carga por primera vez, en contraste con la fase posterior cuando se invoca por primera vez. El analizador no "sabe" que `Int` es un tipo fijo, o que la declaración `r = -r` transforma un `Int` en otro `Int`. La magia de la inferencia de tipos ocurre en la fase posterior de la compilación.

Así, el analizador no sabe que `r` tiene un tipo fijo (`Int`). ni que `r` no cambia de valor una vez que se crea la función interna (por lo que la caja no es necesaria). Por lo tanto, el analizador emite código para una caja que contiene un objeto con un tipo abstracto como `Any`, lo que requiere despacho de tipo en tiempo de ejecución para cada ocurrencia de `r`. Esto se puede verificar aplicando `@code_warntype` a la función anterior. Tanto la caja como el despacho de tipo en tiempo de ejecución pueden causar pérdida de rendimiento.

Si se utilizan variables capturadas en una sección crítica del rendimiento del código, los siguientes consejos ayudan a garantizar que su uso sea eficiente. Primero, si se sabe que una variable capturada no cambia su tipo, entonces esto se puede declarar explícitamente con una anotación de tipo (en la variable, no en el lado derecho):

```julia
function abmult2(r0::Int)
    r::Int = r0
    if r < 0
        r = -r
    end
    f = x -> x * r
    return f
end
```

La anotación de tipo recupera parcialmente el rendimiento perdido debido a la captura porque el analizador puede asociar un tipo concreto al objeto en la caja. Más allá de eso, si la variable capturada no necesita ser encapsulada en absoluto (porque no se reasignará después de que se cree el cierre), esto se puede indicar con bloques `let` de la siguiente manera.

```julia
function abmult3(r::Int)
    if r < 0
        r = -r
    end
    f = let r = r
            x -> x * r
    end
    return f
end
```

El bloque `let` crea una nueva variable `r` cuyo alcance es solo la función interna. La segunda técnica recupera el rendimiento completo del lenguaje en presencia de variables capturadas. Tenga en cuenta que este es un aspecto en rápida evolución del compilador, y es probable que las futuras versiones no requieran este grado de anotación por parte del programador para alcanzar el rendimiento. Mientras tanto, algunos paquetes contribuidos por usuarios como [FastClosures](https://github.com/c42f/FastClosures.jl) automatizan la inserción de declaraciones `let` como en `abmult3`.

## [Multithreading and linear algebra](@id man-multithreading-linear-algebra)

Esta sección se aplica al código de Julia multihilo que, en cada hilo, realiza operaciones de álgebra lineal. De hecho, estas operaciones de álgebra lineal implican llamadas a BLAS / LAPACK, que son multihilo por sí mismas. En este caso, se debe asegurar que los núcleos no estén sobrecargados debido a los dos tipos diferentes de multihilo.

Julia compila y utiliza su propia copia de OpenBLAS para álgebra lineal, cuyo número de hilos se controla mediante la variable de entorno `OPENBLAS_NUM_THREADS`. Se puede establecer como una opción de línea de comandos al iniciar Julia, o modificarse durante la sesión de Julia con `BLAS.set_num_threads(N)` (el submódulo `BLAS` se exporta mediante `using LinearAlgebra`). Su valor actual se puede acceder con `BLAS.get_num_threads()`.

Cuando el usuario no especifica nada, Julia intenta elegir un valor razonable para el número de hilos de OpenBLAS (por ejemplo, basado en la plataforma, la versión de Julia, etc.). Sin embargo, generalmente se recomienda verificar y establecer el valor manualmente. El comportamiento de OpenBLAS es el siguiente:

  * Si `OPENBLAS_NUM_THREADS=1`, OpenBLAS utiliza el(los) hilo(s) de Julia que lo llama(n), es decir, "vive en" el hilo de Julia que ejecuta el cálculo.
  * Si `OPENBLAS_NUM_THREADS=N>1`, OpenBLAS crea y gestiona su propio grupo de hilos (`N` en total). Hay solo un grupo de hilos de OpenBLAS compartido entre todos los hilos de Julia.

Cuando inicias Julia en modo multihilo con `JULIA_NUM_THREADS=X`, generalmente se recomienda establecer `OPENBLAS_NUM_THREADS=1`. Dado el comportamiento descrito anteriormente, aumentar el número de hilos de BLAS a `N>1` puede llevar fácilmente a un peor rendimiento, en particular cuando `N<<X`. Sin embargo, esta es solo una regla general, y la mejor manera de establecer cada número de hilos es experimentar con tu aplicación específica.

## [Alternative linear algebra backends](@id man-backends-linear-algebra)

Como alternativa a OpenBLAS, existen varios otros backends que pueden ayudar con el rendimiento del álgebra lineal. Ejemplos prominentes incluyen [MKL.jl](https://github.com/JuliaLinearAlgebra/MKL.jl) y [AppleAccelerate.jl](https://github.com/JuliaMath/AppleAccelerate.jl).

Estos son paquetes externos, por lo que no los discutiremos en detalle aquí. Por favor, consulta sus respectivas documentaciones (especialmente porque tienen comportamientos diferentes a OpenBLAS con respecto al multihilo).

## Execution latency, package loading and package precompiling time

### Reducing time to first plot etc.

La primera vez que se llama a un método de Julia, este (y cualquier método que llame, o aquellos que se pueden determinar estáticamente) será compilado. La familia de macros [`@time`](@ref) ilustra esto.

```
julia> foo() = rand(2,2) * rand(2,2)
foo (generic function with 1 method)

julia> @time @eval foo();
  0.252395 seconds (1.12 M allocations: 56.178 MiB, 2.93% gc time, 98.12% compilation time)

julia> @time @eval foo();
  0.000156 seconds (63 allocations: 2.453 KiB)
```

Tenga en cuenta que `@time @eval` es mejor para medir el tiempo de compilación porque sin [`@eval`](@ref), es posible que parte de la compilación ya se haya realizado antes de que comience el tiempo.

Al desarrollar un paquete, es posible que puedas mejorar la experiencia de tus usuarios con *precompilación* para que cuando utilicen el paquete, el código que usan ya esté compilado. Para precompilar el código del paquete de manera efectiva, se recomienda usar [`PrecompileTools.jl`](https://julialang.github.io/PrecompileTools.jl/stable/) para ejecutar una "carga de trabajo de precompilación" durante el tiempo de precompilación que sea representativa del uso típico del paquete, lo que almacenará en caché el código nativo compilado en la caché `pkgimage` del paquete, reduciendo significativamente el "tiempo hasta la primera ejecución" (a menudo referido como TTFX) para dicho uso.

Tenga en cuenta que [`PrecompileTools.jl`](https://julialang.github.io/PrecompileTools.jl/stable/) las cargas de trabajo se pueden deshabilitar y, a veces, configurar a través de Preferencias si no desea gastar el tiempo extra en la precompilación, lo cual puede ser el caso durante el desarrollo de un paquete.

### Reducing package loading time

Mantener el tiempo de carga del paquete bajo suele ser útil. Las buenas prácticas generales para los desarrolladores de paquetes incluyen:

1. Reduce tus dependencias a las que realmente necesitas. Considera usar [package extensions](@ref) para apoyar la interoperabilidad con otros paquetes sin aumentar el tamaño de tus dependencias esenciales.
2. Evite el uso de [`__init__()`](@ref) funciones a menos que no haya alternativa, especialmente aquellas que podrían desencadenar mucha compilación, o que simplemente tarden mucho en ejecutarse.
3. Donde sea posible, corrige [invalidations](https://julialang.org/blog/2020/08/invalidations/) entre tus dependencias y en el código de tu paquete.

La herramienta [`@time_imports`](@ref) puede ser útil en el REPL para revisar los factores anteriores.

```julia-repl
julia> @time @time_imports using Plots
      0.5 ms  Printf
     16.4 ms  Dates
      0.7 ms  Statistics
               ┌ 23.8 ms SuiteSparse_jll.__init__() 86.11% compilation time (100% recompilation)
     90.1 ms  SuiteSparse_jll 91.57% compilation time (82% recompilation)
      0.9 ms  Serialization
               ┌ 39.8 ms SparseArrays.CHOLMOD.__init__() 99.47% compilation time (100% recompilation)
    166.9 ms  SparseArrays 23.74% compilation time (100% recompilation)
      0.4 ms  Statistics → SparseArraysExt
      0.5 ms  TOML
      8.0 ms  Preferences
      0.3 ms  PrecompileTools
      0.2 ms  Reexport
... many deps omitted for example ...
      1.4 ms  Tar
               ┌ 73.8 ms p7zip_jll.__init__() 99.93% compilation time (100% recompilation)
     79.4 ms  p7zip_jll 92.91% compilation time (100% recompilation)
               ┌ 27.7 ms GR.GRPreferences.__init__() 99.77% compilation time (100% recompilation)
     43.0 ms  GR 64.26% compilation time (100% recompilation)
               ┌ 2.1 ms Plots.__init__() 91.80% compilation time (100% recompilation)
    300.9 ms  Plots 0.65% compilation time (100% recompilation)
  1.795602 seconds (3.33 M allocations: 190.153 MiB, 7.91% gc time, 39.45% compilation time: 97% of which was recompilation)

```

Tenga en cuenta que en este ejemplo hay múltiples paquetes cargados, algunos con funciones `__init__()`, algunos de los cuales causan compilación, de los cuales algunos son recompilaciones. La recompilación es causada por paquetes anteriores que invalidan métodos, luego en estos casos, cuando los siguientes paquetes ejecutan su función `__init__()`, algunos provocan recompilación antes de que el código pueda ser ejecutado.

Además, ten en cuenta que la extensión `Statistics` `SparseArraysExt` ha sido activada porque `SparseArrays` está en el árbol de dependencias. es decir, ver `0.4 ms  Statistics → SparseArraysExt`.

Este informe ofrece una buena oportunidad para revisar si el costo del tiempo de carga de dependencias vale la funcionalidad que aporta. También se puede utilizar la utilidad `Pkg` `why` para informar por qué existe una dependencia indirecta.

```
(CustomPackage) pkg> why FFMPEG_jll
  Plots → FFMPEG → FFMPEG_jll
  Plots → GR → GR_jll → FFMPEG_jll
```

o para ver las dependencias indirectas que trae un paquete, puedes `pkg> rm` el paquete, ver las dependencias que se eliminan del manifiesto, y luego revertir el cambio con `pkg> undo`.

Si el tiempo de carga está dominado por métodos `__init__()` lentos que tienen compilación, una forma detallada de identificar qué se está compilando es usar los argumentos de julia `--trace-compile=stderr`, que informará una declaración [`precompile`](@ref) cada vez que se compila un método. Por ejemplo, la configuración completa sería:

```
$ julia --startup-file=no --trace-compile=stderr
julia> @time @time_imports using CustomPackage
...
```

Nota el `--startup-file=no` que ayuda a aislar la prueba de los paquetes que puedas tener en tu `startup.jl`.

Un análisis más detallado de las razones para la recompilación se puede lograr con el paquete [`SnoopCompile`](https://github.com/timholy/SnoopCompile.jl).
