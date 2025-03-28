# Multi-processing and Distributed Computing

Una implementación de computación paralela de memoria distribuida es proporcionada por el módulo [`Distributed`](@ref man-distributed) como parte de la biblioteca estándar que se envía con Julia.

La mayoría de las computadoras modernas poseen más de una CPU, y varias computadoras pueden combinarse en un clúster. Aprovechar el poder de estas múltiples CPUs permite que muchos cálculos se completen más rápidamente. Hay dos factores principales que influyen en el rendimiento: la velocidad de las propias CPUs y la velocidad de su acceso a la memoria. En un clúster, es bastante obvio que una CPU determinada tendrá el acceso más rápido a la RAM dentro de la misma computadora (nodo). Quizás más sorprendentemente, problemas similares son relevantes en una laptop multicore típica, debido a las diferencias en la velocidad de la memoria principal y el [cache](https://www.akkadia.org/drepper/cpumemory.pdf). En consecuencia, un buen entorno de multiprocesamiento debería permitir el control sobre la "propiedad" de un bloque de memoria por una CPU particular. Julia proporciona un entorno de multiprocesamiento basado en el paso de mensajes para permitir que los programas se ejecuten en múltiples procesos en dominios de memoria separados a la vez.

La implementación de paso de mensajes de Julia es diferente de otros entornos como MPI[^1]. La comunicación en Julia es generalmente "unilateral", lo que significa que el programador necesita gestionar explícitamente solo un proceso en una operación de dos procesos. Además, estas operaciones típicamente no se parecen a "enviar mensaje" y "recibir mensaje", sino que se asemejan a operaciones de nivel superior como llamadas a funciones de usuario.

La programación distribuida en Julia se basa en dos primitivas: *referencias remotas* y *llamadas remotas*. Una referencia remota es un objeto que puede ser utilizado desde cualquier proceso para referirse a un objeto almacenado en un proceso particular. Una llamada remota es una solicitud de un proceso para llamar a una cierta función con ciertos argumentos en otro proceso (posiblemente el mismo).

Las referencias remotas vienen en dos sabores: [`Future`](@ref Distributed.Future) y [`RemoteChannel`](@ref).

Una llamada remota devuelve un [`Future`](@ref Distributed.Future) a su resultado. Las llamadas remotas devuelven inmediatamente; el proceso que realizó la llamada procede a su siguiente operación mientras la llamada remota ocurre en otro lugar. Puedes esperar a que una llamada remota termine llamando a [`wait`](@ref) en el `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` devuelto, y puedes obtener el valor completo del resultado usando [`fetch`](@ref).

Por otro lado, [`RemoteChannel`](@ref) s son reescribibles. Por ejemplo, múltiples procesos pueden coordinar su procesamiento haciendo referencia al mismo `Channel` remoto.

Cada proceso tiene un identificador asociado. El proceso que proporciona el aviso interactivo de Julia siempre tiene un `id` igual a 1. Los procesos utilizados por defecto para operaciones en paralelo se denominan "trabajadores". Cuando solo hay un proceso, el proceso 1 se considera un trabajador. De lo contrario, los trabajadores se consideran todos los procesos que no son el proceso 1. Como resultado, se requiere agregar 2 o más procesos para obtener beneficios de métodos de procesamiento en paralelo como [`pmap`](@ref). Agregar un solo proceso es beneficioso si solo deseas hacer otras cosas en el proceso principal mientras se ejecuta un cálculo largo en el trabajador.

Comencemos con `julia -p n`, que proporciona `n` procesos de trabajo en la máquina local. Generalmente, tiene sentido que `n` sea igual al número de hilos de CPU (núcleos lógicos) en la máquina. Tenga en cuenta que el argumento `-p` carga implícitamente el módulo [`Distributed`](@ref man-distributed).

```julia
$ julia -p 2

julia> r = remotecall(rand, 2, 2, 2)
Future(2, 1, 4, nothing)

julia> s = @spawnat 2 1 .+ fetch(r)
Future(2, 1, 5, nothing)

julia> fetch(s)
2×2 Array{Float64,2}:
 1.18526  1.50912
 1.16296  1.60607
```

El primer argumento de [`remotecall`](@ref) es la función a llamar. La mayoría de la programación paralela en Julia no hace referencia a procesos específicos o al número de procesos disponibles, pero `4d61726b646f776e2e436f64652822222c202272656d6f746563616c6c2229_40726566` se considera una interfaz de bajo nivel que proporciona un control más fino. El segundo argumento de `4d61726b646f776e2e436f64652822222c202272656d6f746563616c6c2229_40726566` es el `id` del proceso que realizará el trabajo, y los argumentos restantes se pasarán a la función que se está llamando.

Como puedes ver, en la primera línea pedimos al proceso 2 que construyera una matriz aleatoria de 2 por 2, y en la segunda línea le pedimos que le añadiera 1. El resultado de ambos cálculos está disponible en los dos futuros, `r` y `s`. El macro [`@spawnat`](@ref) evalúa la expresión en el segundo argumento en el proceso especificado por el primer argumento.

Ocasionalmente, es posible que desees un valor calculado de forma remota de inmediato. Esto suele ocurrir cuando lees de un objeto remoto para obtener datos necesarios para la siguiente operación local. La función [`remotecall_fetch`](@ref) existe para este propósito. Es equivalente a `fetch(remotecall(...))`, pero es más eficiente.

```julia-repl
julia> remotecall_fetch(r-> fetch(r)[1, 1], 2, r)
0.18526337335308085
```

Esto obtiene el arreglo en el trabajador 2 y devuelve el primer valor. Ten en cuenta que `fetch` no mueve ningún dato en este caso, ya que se ejecuta en el trabajador que posee el arreglo. También se puede escribir:

```julia-repl
julia> remotecall_fetch(getindex, 2, r, 1, 1)
0.10824216411304866
```

Recuerda que [`getindex(r,1,1)`](@ref) es [equivalent](@ref man-array-indexing) para `r[1,1]`, así que esta llamada obtiene el primer elemento del futuro `r`.

Para facilitar las cosas, el símbolo `:any` se puede pasar a [`@spawnat`](@ref), que elige dónde realizar la operación por ti:

```julia-repl
julia> r = @spawnat :any rand(2,2)
Future(2, 1, 4, nothing)

julia> s = @spawnat :any 1 .+ fetch(r)
Future(3, 1, 5, nothing)

julia> fetch(s)
2×2 Array{Float64,2}:
 1.38854  1.9098
 1.20939  1.57158
```

Tenga en cuenta que usamos `1 .+ fetch(r)` en lugar de `1 .+ r`. Esto se debe a que no sabemos dónde se ejecutará el código, por lo que en general podría ser necesario un [`fetch`](@ref) para mover `r` al proceso que realiza la adición. En este caso, [`@spawnat`](@ref) es lo suficientemente inteligente como para realizar el cálculo en el proceso que posee `r`, por lo que el `4d61726b646f776e2e436f64652822222c202266657463682229_40726566` será una no-op (no se realiza ningún trabajo).

(Es importante señalar que [`@spawnat`](@ref) no es incorporado, sino definido en Julia como un [macro](@ref man-macros). Es posible definir tus propios constructos de este tipo.)

Una cosa importante a recordar es que, una vez recuperado, un [`Future`](@ref Distributed.Future) almacenará su valor localmente. Las llamadas posteriores [`fetch`](@ref) no implican un salto de red. Una vez que todas las referencias a `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` han sido recuperadas, el valor almacenado de forma remota se elimina.

[`@async`](@ref) es similar a [`@spawnat`](@ref), pero solo ejecuta tareas en el proceso local. Lo usamos para crear una tarea "alimentadora" para cada proceso. Cada tarea toma el siguiente índice que necesita ser computado, luego espera a que su proceso termine, y luego repite hasta que se acaben los índices. Tenga en cuenta que las tareas alimentadoras no comienzan a ejecutarse hasta que la tarea principal alcanza el final del bloque [`@sync`](@ref), momento en el cual cede el control y espera a que todas las tareas locales se completen antes de regresar de la función. En cuanto a v0.7 y versiones posteriores, las tareas alimentadoras pueden compartir estado a través de `nextidx` porque todas se ejecutan en el mismo proceso. Incluso si las `Tasks` se programan de manera cooperativa, el bloqueo puede ser necesario en algunos contextos, como en [asynchronous I/O](@ref faq-async-io). Esto significa que los cambios de contexto solo ocurren en puntos bien definidos: en este caso, cuando se llama a [`remotecall_fetch`](@ref). Este es el estado actual de la implementación y puede cambiar para futuras versiones de Julia, ya que se pretende que sea posible ejecutar hasta N `Tasks` en M `Process`, también conocido como [M:N Threading](https://en.wikipedia.org/wiki/Thread_(computing)#Models). Entonces, se necesitará un modelo de adquisición/liberación de bloqueo para `nextidx`, ya que no es seguro permitir que múltiples procesos lean y escriban un recurso al mismo tiempo.

## [Code Availability and Loading Packages](@id code-availability)

Tu código debe estar disponible en cualquier proceso que lo ejecute. Por ejemplo, escribe lo siguiente en el aviso de Julia:

```julia-repl
julia> function rand2(dims...)
           return 2*rand(dims...)
       end

julia> rand2(2,2)
2×2 Array{Float64,2}:
 0.153756  0.368514
 1.15119   0.918912

julia> fetch(@spawnat :any rand2(2,2))
ERROR: RemoteException(2, CapturedException(UndefVarError(Symbol("#rand2"))))
Stacktrace:
[...]
```

El proceso 1 conocía la función `rand2`, pero el proceso 2 no.

La mayoría de las veces cargarás código desde archivos o paquetes, y tienes una cantidad considerable de flexibilidad para controlar qué procesos cargan código. Considera un archivo, `DummyModule.jl`, que contiene el siguiente código:

```julia
module DummyModule

export MyType, f

mutable struct MyType
    a::Int
end

f(x) = x^2+1

println("loaded")

end
```

Para referirse a `MyType` en todos los procesos, `DummyModule.jl` debe ser cargado en cada proceso. Llamar a `include("DummyModule.jl")` lo carga solo en un único proceso. Para cargarlo en cada proceso, utiliza el macro [`@everywhere`](@ref) (iniciando Julia con `julia -p 2`):

```julia-repl
julia> @everywhere include("DummyModule.jl")
loaded
      From worker 3:    loaded
      From worker 2:    loaded
```

Como de costumbre, esto no trae `DummyModule` al ámbito de ninguno de los procesos, lo que requiere [`using`](@ref) o [`import`](@ref). Además, cuando `DummyModule` se trae al ámbito de un proceso, no lo está en ningún otro:

```julia-repl
julia> using .DummyModule

julia> MyType(7)
MyType(7)

julia> fetch(@spawnat 2 MyType(7))
ERROR: On worker 2:
UndefVarError: `MyType` not defined in `Main`
⋮

julia> fetch(@spawnat 2 DummyModule.MyType(7))
MyType(7)
```

Sin embargo, todavía es posible, por ejemplo, enviar un `MyType` a un proceso que ha cargado `DummyModule` incluso si no está en el ámbito:

```julia-repl
julia> put!(RemoteChannel(2), MyType(7))
RemoteChannel{Channel{Any}}(2, 1, 13)
```

Un archivo también se puede precargar en múltiples procesos al inicio con la bandera `-L`, y se puede utilizar un script de controlador para impulsar el cálculo:

```
julia -p <n> -L file1.jl -L file2.jl driver.jl
```

El proceso de Julia que ejecuta el script del controlador en el ejemplo anterior tiene un `id` igual a 1, al igual que un proceso que proporciona un aviso interactivo.

Finalmente, si `DummyModule.jl` no es un archivo independiente sino un paquete, entonces `using DummyModule` *cargará* `DummyModule.jl` en todos los procesos, pero solo lo traerá al ámbito en el proceso donde se llamó [`using`](@ref).

## Starting and managing worker processes

La instalación base de Julia tiene soporte incorporado para dos tipos de clústeres:

  * Un clúster local especificado con la opción `-p` como se muestra arriba.
  * Un clúster que abarca máquinas utilizando la opción `--machine-file`. Esto utiliza un inicio de sesión `ssh` sin contraseña para iniciar procesos de trabajo de Julia (desde la misma ruta que el host actual) en las máquinas especificadas. Cada definición de máquina toma la forma `[count*][user@]host[:port] [bind_addr[:port]]`. `user` se establece de forma predeterminada en el usuario actual, `port` en el puerto estándar de ssh. `count` es el número de trabajadores que se generarán en el nodo, y por defecto es 1. El opcional `bind-to bind_addr[:port]` especifica la dirección IP y el puerto que otros trabajadores deben usar para conectarse a este trabajador.

!!! note
    Mientras que Julia generalmente se esfuerza por la compatibilidad hacia atrás, la distribución de código a los procesos de trabajo depende de [`Serialization.serialize`](@ref). Como se señala en la documentación correspondiente, esto no se puede garantizar que funcione en diferentes versiones de Julia, por lo que se aconseja que todos los trabajadores en todas las máquinas utilicen la misma versión.


Las funciones [`addprocs`](@ref), [`rmprocs`](@ref), [`workers`](@ref), y otras están disponibles como un medio programático para agregar, eliminar y consultar los procesos en un clúster.

```julia-repl
julia> using Distributed

julia> addprocs(2)
2-element Array{Int64,1}:
 2
 3
```

El módulo [`Distributed`](@ref man-distributed) debe ser cargado explícitamente en el proceso maestro antes de invocar [`addprocs`](@ref). Se hace disponible automáticamente en los procesos de trabajo.

!!! note
    Tenga en cuenta que los trabajadores no ejecutan un script de inicio `~/.julia/config/startup.jl`, ni sincronizan su estado global (como los interruptores de línea de comandos, variables globales, definiciones de nuevos métodos y módulos cargados) con ninguno de los otros procesos en ejecución. Puede usar `addprocs(exeflags="--project")` para inicializar un trabajador con un entorno particular, y luego `@everywhere using <modulename>` o `@everywhere include("file.jl")`.


Otros tipos de clústeres pueden ser compatibles al escribir tu propio `ClusterManager`, como se describe a continuación en la sección [ClusterManagers](@ref).

## Data Movement

Enviar mensajes y mover datos constituyen la mayor parte de la sobrecarga en un programa distribuido. Reducir el número de mensajes y la cantidad de datos enviados es fundamental para lograr rendimiento y escalabilidad. Con este fin, es importante entender el movimiento de datos realizado por las diversas construcciones de programación distribuida de Julia.

[`fetch`](@ref) puede considerarse una operación de movimiento de datos explícita, ya que solicita directamente que un objeto se mueva a la máquina local. [`@spawnat`](@ref) (y algunos constructos relacionados) también mueve datos, pero esto no es tan obvio, por lo que se puede llamar una operación de movimiento de datos implícita. Considere estos dos enfoques para construir y elevar al cuadrado una matriz aleatoria:

Método 1:

```julia-repl
julia> A = rand(1000,1000);

julia> Bref = @spawnat :any A^2;

[...]

julia> fetch(Bref);
```

Método 2:

```julia-repl
julia> Bref = @spawnat :any rand(1000,1000)^2;

[...]

julia> fetch(Bref);
```

La diferencia parece trivial, pero de hecho es bastante significativa debido al comportamiento de [`@spawnat`](@ref). En el primer método, se construye una matriz aleatoria localmente, que luego se envía a otro proceso donde se eleva al cuadrado. En el segundo método, una matriz aleatoria se construye y se eleva al cuadrado en otro proceso. Por lo tanto, el segundo método envía muchos menos datos que el primero.

En este ejemplo de juguete, los dos métodos son fáciles de distinguir y elegir. Sin embargo, en un programa real, diseñar el movimiento de datos podría requerir más reflexión y probablemente alguna medición. Por ejemplo, si el primer proceso necesita la matriz `A`, entonces el primer método podría ser mejor. O, si calcular `A` es costoso y solo el proceso actual lo tiene, entonces moverlo a otro proceso podría ser inevitable. O, si el proceso actual tiene muy poco que hacer entre el [`@spawnat`](@ref) y `fetch(Bref)`, podría ser mejor eliminar el paralelismo por completo. O imagina que `rand(1000,1000)` es reemplazado por una operación más costosa. Entonces podría tener sentido agregar otra declaración `4d61726b646f776e2e436f64652822222c202240737061776e61742229_40726566` solo para este paso.

## Global variables

Las expresiones ejecutadas de forma remota a través de [`@spawnat`](@ref), o los cierres especificados para la ejecución remota utilizando [`remotecall`](@ref) pueden referirse a variables globales. Las vinculaciones globales bajo el módulo `Main` se tratan de manera un poco diferente en comparación con las vinculaciones globales en otros módulos. Considera el siguiente fragmento de código:

```julia-repl
A = rand(10,10)
remotecall_fetch(()->sum(A), 2)
```

En este caso, [`sum`](@ref) DEBE estar definido en el proceso remoto. Tenga en cuenta que `A` es una variable global definida en el espacio de trabajo local. El trabajador 2 no tiene una variable llamada `A` bajo `Main`. El acto de enviar el cierre `()->sum(A)` al trabajador 2 resulta en que `Main.A` se defina en 2. `Main.A` continúa existiendo en el trabajador 2 incluso después de que la llamada [`remotecall_fetch`](@ref) regrese. Las llamadas remotas con referencias globales incrustadas (solo bajo el módulo `Main`) gestionan las globales de la siguiente manera:

  * Se crean nuevos enlaces globales en los trabajadores de destino si se hacen referencia a ellos como parte de una llamada remota.
  * Las constantes globales se declaran como constantes en los nodos remotos también.
  * Los globales se reenvían a un trabajador de destino solo en el contexto de una llamada remota, y solo si su valor ha cambiado. Además, el clúster no sincroniza los enlaces globales entre nodos. Por ejemplo:

    ```julia
    A = rand(10,10)
    remotecall_fetch(()->sum(A), 2) # worker 2
    A = rand(10,10)
    remotecall_fetch(()->sum(A), 3) # worker 3
    A = nothing
    ```

    Ejecutar el fragmento anterior resulta en que `Main.A` en el trabajador 2 tiene un valor diferente de `Main.A` en el trabajador 3, mientras que el valor de `Main.A` en el nodo 1 se establece en `nada`.

Como puede haber notado, mientras que la memoria asociada con los globales puede ser recolectada cuando se reasignan en el maestro, no se toma tal acción en los trabajadores ya que los enlaces continúan siendo válidos. [`clear!`](@ref) se puede usar para reasignar manualmente globals específicos en nodos remotos a `nothing` una vez que ya no son necesarios. Esto liberará cualquier memoria asociada con ellos como parte de un ciclo regular de recolección de basura.

Por lo tanto, los programas deben tener cuidado al referenciar variables globales en llamadas remotas. De hecho, es preferible evitarlas por completo si es posible. Si debes referenciar variables globales, considera usar bloques `let` para localizar las variables globales.

Por ejemplo:

```julia-repl
julia> A = rand(10,10);

julia> remotecall_fetch(()->A, 2);

julia> B = rand(10,10);

julia> let B = B
           remotecall_fetch(()->B, 2)
       end;

julia> @fetchfrom 2 InteractiveUtils.varinfo()
name           size summary
––––––––– ––––––––– ––––––––––––––––––––––
A         800 bytes 10×10 Array{Float64,2}
Base                Module
Core                Module
Main                Module
```

Como se puede ver, la variable global `A` está definida en el trabajador 2, pero `B` se captura como una variable local y, por lo tanto, no existe un enlace para `B` en el trabajador 2.

## Parallel Map and Loops

Fortunately, many useful parallel computations do not require data movement. A common example is a Monte Carlo simulation, where multiple processes can handle independent simulation trials simultaneously. We can use [`@spawnat`](@ref) to flip coins on two processes. First, write the following function in `count_heads.jl`:

```julia
function count_heads(n)
    c::Int = 0
    for i = 1:n
        c += rand(Bool)
    end
    c
end
```

La función `count_heads` simplemente suma `n` bits aleatorios. Aquí se muestra cómo podemos realizar algunas pruebas en dos máquinas y sumar los resultados:

```julia-repl
julia> @everywhere include_string(Main, $(read("count_heads.jl", String)), "count_heads.jl")

julia> a = @spawnat :any count_heads(100000000)
Future(2, 1, 6, nothing)

julia> b = @spawnat :any count_heads(100000000)
Future(3, 1, 7, nothing)

julia> fetch(a)+fetch(b)
100001564
```

Este ejemplo demuestra un patrón de programación paralela poderoso y a menudo utilizado. Muchas iteraciones se ejecutan de manera independiente en varios procesos, y luego sus resultados se combinan utilizando alguna función. El proceso de combinación se llama *reducción*, ya que generalmente reduce el rango del tensor: un vector de números se reduce a un solo número, o una matriz se reduce a una sola fila o columna, etc. En código, esto típicamente se ve como el patrón `x = f(x,v[i])`, donde `x` es el acumulador, `f` es la función de reducción, y los `v[i]` son los elementos que se están reduciendo. Es deseable que `f` sea asociativa, de modo que no importe el orden en que se realicen las operaciones.

Tenga en cuenta que nuestro uso de este patrón con `count_heads` se puede generalizar. Utilizamos dos declaraciones explícitas [`@spawnat`](@ref), lo que limita el paralelismo a dos procesos. Para ejecutar en cualquier número de procesos, podemos usar un *bucle for paralelo*, que se ejecuta en memoria distribuida, que se puede escribir en Julia usando [`@distributed`](@ref) de la siguiente manera:

```julia
nheads = @distributed (+) for i = 1:200000000
    Int(rand(Bool))
end
```

Este constructo implementa el patrón de asignar iteraciones a múltiples procesos y combinarlas con una reducción especificada (en este caso `(+)`). El resultado de cada iteración se toma como el valor de la última expresión dentro del bucle. La expresión completa del bucle paralelo se evalúa como la respuesta final.

Tenga en cuenta que, aunque los bucles for paralelos se parecen a los bucles for seriales, su comportamiento es drásticamente diferente. En particular, las iteraciones no ocurren en un orden específico, y las escrituras en variables o arreglos no serán visibles globalmente, ya que las iteraciones se ejecutan en diferentes procesos. Cualquier variable utilizada dentro del bucle paralelo será copiada y transmitida a cada proceso.

Por ejemplo, el siguiente código no funcionará como se esperaba:

```julia
a = zeros(100000)
@distributed for i = 1:100000
    a[i] = i
end
```

Este código no inicializará todo `a`, ya que cada proceso tendrá una copia separada de él. Los bucles paralelos como estos deben ser evitados. Afortunadamente, [Shared Arrays](@ref man-shared-arrays) se puede usar para sortear esta limitación:

```julia
using SharedArrays

a = SharedArray{Float64}(10)
@distributed for i = 1:10
    a[i] = i
end
```

Usar variables "externas" en bucles paralelos es perfectamente razonable si las variables son de solo lectura:

```julia
a = randn(1000)
@distributed (+) for i = 1:100000
    f(a[rand(1:end)])
end
```

Aquí, cada iteración aplica `f` a una muestra elegida al azar de un vector `a` compartido por todos los procesos.

Como puedes ver, el operador de reducción se puede omitir si no es necesario. En ese caso, el bucle se ejecuta de manera asíncrona, es decir, genera tareas independientes en todos los trabajadores disponibles y devuelve un array de [`Future`](@ref Distributed.Future) inmediatamente sin esperar a que se complete. El llamador puede esperar las finalizaciones de `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` en un momento posterior llamando a [`fetch`](@ref) sobre ellas, o esperar la finalización al final del bucle prefijándolo con [`@sync`](@ref), como `@sync @distributed for`.

En algunos casos, no se necesita un operador de reducción, y simplemente deseamos aplicar una función a todos los enteros en algún rango (o, más generalmente, a todos los elementos en alguna colección). Esta es otra operación útil llamada *mapa paralelo*, implementada en Julia como la función [`pmap`](@ref). Por ejemplo, podríamos calcular los valores singulares de varias matrices aleatorias grandes en paralelo de la siguiente manera:

```julia-repl
julia> M = Matrix{Float64}[rand(1000,1000) for i = 1:10];

julia> pmap(svdvals, M);
```

El [`pmap`](@ref) de Julia está diseñado para el caso en el que cada llamada a la función realiza una gran cantidad de trabajo. En contraste, `@distributed for` puede manejar situaciones donde cada iteración es pequeña, quizás simplemente sumando dos números. Solo se utilizan procesos de trabajo tanto en `4d61726b646f776e2e436f64652822222c2022706d61702229_40726566` como en `@distributed for` para la computación paralela. En el caso de `@distributed for`, la reducción final se realiza en el proceso que llama.

## Remote References and AbstractChannels

Las referencias remotas siempre se refieren a una implementación de un `AbstractChannel`.

Una implementación concreta de un `AbstractChannel` (como `Channel`), debe implementar [`put!`](@ref), [`take!`](@ref), [`fetch`](@ref), [`isready`](@ref) y [`wait`](@ref). El objeto remoto al que se refiere un [`Future`](@ref Distributed.Future) se almacena en un `Channel{Any}(1)`, es decir, un `Channel` de tamaño 1 capaz de contener objetos de tipo `Any`.

[`RemoteChannel`](@ref), que es reescribible, puede apuntar a cualquier tipo y tamaño de canales, o cualquier otra implementación de un `AbstractChannel`.

El constructor `RemoteChannel(f::Function, pid)()` nos permite construir referencias a canales que contienen más de un valor de un tipo específico. `f` es una función que se ejecuta en `pid` y debe devolver un `AbstractChannel`.

Por ejemplo, `RemoteChannel(()->Channel{Int}(10), pid)`, devolverá una referencia a un canal de tipo `Int` y tamaño 10. El canal existe en el trabajador `pid`.

Los métodos [`put!`](@ref), [`take!`](@ref), [`fetch`](@ref), [`isready`](@ref) y [`wait`](@ref) en un [`RemoteChannel`](@ref) están proxied en el almacenamiento de respaldo en el proceso remoto.

[`RemoteChannel`](@ref) puede usarse para referirse a objetos `AbstractChannel` implementados por el usuario. Un ejemplo simple de esto es el siguiente `DictChannel`, que utiliza un diccionario como su almacenamiento remoto:

```jldoctest
julia> struct DictChannel{T} <: AbstractChannel{T}
           d::Dict
           cond_take::Threads.Condition    # waiting for data to become available
           DictChannel{T}() where {T} = new(Dict(), Threads.Condition())
           DictChannel() = DictChannel{Any}()
       end

julia> begin
       function Base.put!(D::DictChannel, k, v)
           @lock D.cond_take begin
               D.d[k] = v
               notify(D.cond_take)
           end
           return D
       end
       function Base.take!(D::DictChannel, k)
           @lock D.cond_take begin
               v = fetch(D, k)
               delete!(D.d, k)
               return v
           end
       end
       Base.isready(D::DictChannel) = @lock D.cond_take !isempty(D.d)
       Base.isready(D::DictChannel, k) = @lock D.cond_take haskey(D.d, k)
       function Base.fetch(D::DictChannel, k)
           @lock D.cond_take begin
               wait(D, k)
               return D.d[k]
           end
       end
       function Base.wait(D::DictChannel, k)
           @lock D.cond_take begin
               while !isready(D, k)
                   wait(D.cond_take)
               end
           end
       end
       end;

julia> d = DictChannel();

julia> isready(d)
false

julia> put!(d, :k, :v);

julia> isready(d, :k)
true

julia> fetch(d, :k)
:v

julia> wait(d, :k)

julia> take!(d, :k)
:v

julia> isready(d, :k)
false
```

## Channels and RemoteChannels

  * Un [`Channel`](@ref) es local a un proceso. El trabajador 2 no puede referirse directamente a un `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` en el trabajador 3 y viceversa. Sin embargo, un [`RemoteChannel`](@ref) puede poner y tomar valores entre trabajadores.
  * Un [`RemoteChannel`](@ref) puede ser pensado como un *mango* para un [`Channel`](@ref).
  * El id de proceso, `pid`, asociado con un [`RemoteChannel`](@ref) identifica el proceso donde existe el almacenamiento de respaldo, es decir, el [`Channel`](@ref).
  * Cualquier proceso con una referencia a un [`RemoteChannel`](@ref) puede poner y tomar elementos del canal. Los datos se envían automáticamente a (o se recuperan de) el proceso con el que está asociado un `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566`.
  * Serializar un [`Channel`](@ref) también serializa cualquier dato presente en el canal. Deserializarlo, por lo tanto, efectivamente hace una copia del objeto original.
  * Por otro lado, la serialización de un [`RemoteChannel`](@ref) solo implica la serialización de un identificador que identifica la ubicación y la instancia de [`Channel`](@ref) al que se hace referencia mediante el identificador. Un objeto `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` deserializado (en cualquier trabajador), por lo tanto, también apunta al mismo almacenamiento de respaldo que el original.

El ejemplo de canales de arriba se puede modificar para la comunicación entre procesos, como se muestra a continuación.

Iniciamos 4 trabajadores para procesar un único canal remoto de `jobs`. Los trabajos, identificados por un id (`job_id`), se escriben en el canal. Cada tarea que se ejecuta de forma remota en esta simulación lee un `job_id`, espera un tiempo aleatorio y escribe de vuelta una tupla de `job_id`, tiempo tomado y su propio `pid` en el canal de resultados. Finalmente, todos los `resultados` se imprimen en el proceso maestro.

```julia-repl
julia> addprocs(4); # add worker processes

julia> const jobs = RemoteChannel(()->Channel{Int}(32));

julia> const results = RemoteChannel(()->Channel{Tuple}(32));

julia> @everywhere function do_work(jobs, results) # define work function everywhere
           while true
               job_id = take!(jobs)
               exec_time = rand()
               sleep(exec_time) # simulates elapsed time doing actual work
               put!(results, (job_id, exec_time, myid()))
           end
       end

julia> function make_jobs(n)
           for i in 1:n
               put!(jobs, i)
           end
       end;

julia> n = 12;

julia> errormonitor(@async make_jobs(n)); # feed the jobs channel with "n" jobs

julia> for p in workers() # start tasks on the workers to process requests in parallel
           remote_do(do_work, p, jobs, results)
       end

julia> @elapsed while n > 0 # print out results
           job_id, exec_time, where = take!(results)
           println("$job_id finished in $(round(exec_time; digits=2)) seconds on worker $where")
           global n = n - 1
       end
1 finished in 0.18 seconds on worker 4
2 finished in 0.26 seconds on worker 5
6 finished in 0.12 seconds on worker 4
7 finished in 0.18 seconds on worker 4
5 finished in 0.35 seconds on worker 5
4 finished in 0.68 seconds on worker 2
3 finished in 0.73 seconds on worker 3
11 finished in 0.01 seconds on worker 3
12 finished in 0.02 seconds on worker 3
9 finished in 0.26 seconds on worker 5
8 finished in 0.57 seconds on worker 4
10 finished in 0.58 seconds on worker 2
0.055971741
```

### Remote References and Distributed Garbage Collection

Los objetos a los que se hace referencia mediante referencias remotas solo pueden liberarse cuando se eliminan *todas* las referencias mantenidas en el clúster.

El nodo donde se almacena el valor lleva un registro de cuáles de los trabajadores tienen una referencia a él. Cada vez que un [`RemoteChannel`](@ref) o un [`Future`](@ref Distributed.Future) (no recuperado) se serializa a un trabajador, se notifica al nodo apuntado por la referencia. Y cada vez que un `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` o un `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` (no recuperado) se recolecta como basura localmente, el nodo que posee el valor es nuevamente notificado. Esto se implementa en un serializador interno consciente del clúster. Las referencias remotas solo son válidas en el contexto de un clúster en funcionamiento. No se admite la serialización y deserialización de referencias a y desde objetos `IO` regulares.

Las notificaciones se realizan mediante el envío de mensajes de "seguimiento": un mensaje de "agregar referencia" cuando una referencia se serializa a un proceso diferente y un mensaje de "eliminar referencia" cuando una referencia se recolecta localmente.

Dado que [`Future`](@ref Distributed.Future) son de escritura única y se almacenan en caché localmente, el acto de [`fetch`](@ref) de un `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` también actualiza la información de seguimiento de referencias en el nodo que posee el valor.

El nodo que posee el valor lo libera una vez que se eliminan todas las referencias a él.

Con [`Future`](@ref Distributed.Future), serializar un `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` ya recuperado a un nodo diferente también envía el valor, ya que la tienda remota original puede haber recopilado el valor para este momento.

Es importante tener en cuenta que *cuándo* un objeto se recolecta como basura localmente depende del tamaño del objeto y de la presión de memoria actual en el sistema.

En caso de referencias remotas, el tamaño del objeto de referencia local es bastante pequeño, mientras que el valor almacenado en el nodo remoto puede ser bastante grande. Dado que el objeto local puede no ser recolectado de inmediato, es una buena práctica llamar explícitamente a [`finalize`](@ref) en instancias locales de un [`RemoteChannel`](@ref), o en [`Future`](@ref Distributed.Future)s no recuperados. Dado que llamar a [`fetch`](@ref) en un `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` también elimina su referencia de la tienda remota, esto no es necesario en `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265`s recuperados. Llamar explícitamente a `4d61726b646f776e2e436f64652822222c202266696e616c697a652229_40726566` resulta en un mensaje inmediato enviado al nodo remoto para proceder a eliminar su referencia al valor.

Una vez finalizada, una referencia se vuelve inválida y no se puede usar en ninguna llamada posterior.

## Local invocations

Los datos se copian necesariamente al nodo remoto para su ejecución. Este es el caso tanto para las llamadas remotas como cuando los datos se almacenan en un [`RemoteChannel`](@ref) / [`Future`](@ref Distributed.Future) en un nodo diferente. Como se esperaba, esto resulta en una copia de los objetos serializados en el nodo remoto. Sin embargo, cuando el nodo de destino es el nodo local, es decir, el id del proceso que llama es el mismo que el id del nodo remoto, se ejecuta como una llamada local. Generalmente (no siempre) se ejecuta en una tarea diferente, pero no hay serialización/deserialización de datos. En consecuencia, la llamada se refiere a las mismas instancias de objeto que se pasaron; no se crean copias. Este comportamiento se destaca a continuación:

```julia-repl
julia> using Distributed;

julia> rc = RemoteChannel(()->Channel(3));   # RemoteChannel created on local node

julia> v = [0];

julia> for i in 1:3
           v[1] = i                          # Reusing `v`
           put!(rc, v)
       end;

julia> result = [take!(rc) for _ in 1:3];

julia> println(result);
Array{Int64,1}[[3], [3], [3]]

julia> println("Num Unique objects : ", length(unique(map(objectid, result))));
Num Unique objects : 1

julia> addprocs(1);

julia> rc = RemoteChannel(()->Channel(3), workers()[1]);   # RemoteChannel created on remote node

julia> v = [0];

julia> for i in 1:3
           v[1] = i
           put!(rc, v)
       end;

julia> result = [take!(rc) for _ in 1:3];

julia> println(result);
Array{Int64,1}[[1], [2], [3]]

julia> println("Num Unique objects : ", length(unique(map(objectid, result))));
Num Unique objects : 3
```

Como se puede ver, [`put!`](@ref) en un [`RemoteChannel`](@ref) de propiedad local con el mismo objeto `v` modificado entre llamadas resulta en la misma instancia de objeto única almacenada. A diferencia de las copias de `v` que se crean cuando el nodo que posee `rc` es un nodo diferente.

Cabe señalar que esto generalmente no es un problema. Es algo que solo debe tenerse en cuenta si el objeto se almacena localmente y se modifica después de la llamada. En tales casos, puede ser apropiado almacenar una `deepcopy` del objeto.

Esto también es cierto para las llamadas remotas en el nodo local, como se ve en el siguiente ejemplo:

```julia-repl
julia> using Distributed; addprocs(1);

julia> v = [0];

julia> v2 = remotecall_fetch(x->(x[1] = 1; x), myid(), v);     # Executed on local node

julia> println("v=$v, v2=$v2, ", v === v2);
v=[1], v2=[1], true

julia> v = [0];

julia> v2 = remotecall_fetch(x->(x[1] = 1; x), workers()[1], v); # Executed on remote node

julia> println("v=$v, v2=$v2, ", v === v2);
v=[0], v2=[1], false
```

Como se puede ver una vez más, una llamada remota al nodo local se comporta exactamente como una invocación directa. La llamada modifica los objetos locales pasados como argumentos. En la invocación remota, opera sobre una copia de los argumentos.

Para repetir, en general esto no es un problema. Si el nodo local también se está utilizando como un nodo de cómputo, y los argumentos utilizados después de la llamada, este comportamiento debe tenerse en cuenta y, si es necesario, se deben pasar copias profundas de los argumentos a la llamada invocada en el nodo local. Las llamadas en nodos remotos siempre operarán sobre copias de los argumentos.

## [Shared Arrays](@id man-shared-arrays)

Los Arrays Compartidos utilizan la memoria compartida del sistema para mapear el mismo array en muchos procesos. Un [`SharedArray`](@ref) es una buena opción cuando deseas tener una gran cantidad de datos accesibles conjuntamente para dos o más procesos en la misma máquina. El soporte para Arrays Compartidos está disponible a través del módulo `SharedArrays`, que debe ser cargado explícitamente en todos los trabajadores participantes.

Una estructura de datos complementaria es proporcionada por el paquete externo [`DistributedArrays.jl`](https://github.com/JuliaParallel/DistributedArrays.jl) en forma de un `DArray`. Si bien hay algunas similitudes con un [`SharedArray`](@ref), el comportamiento de un [`DArray`](https://github.com/JuliaParallel/DistributedArrays.jl) es bastante diferente. En un `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566`, cada proceso "participante" tiene acceso a toda la matriz; en contraste, en un `4d61726b646f776e2e436f64652822222c20224441727261792229_68747470733a2f2f6769746875622e636f6d2f4a756c6961506172616c6c656c2f44697374726962757465644172726179732e6a6c`, cada proceso tiene acceso local a solo un fragmento de los datos, y ningún par de procesos comparte el mismo fragmento.

[`SharedArray`](@ref) la indexación (asignación y acceso a valores) funciona igual que con arreglos regulares, y es eficiente porque la memoria subyacente está disponible para el proceso local. Por lo tanto, la mayoría de los algoritmos funcionan de manera natural en `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566`, aunque en modo de un solo proceso. En los casos en que un algoritmo insiste en una entrada de [`Array`](@ref), el arreglo subyacente se puede recuperar de un `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566` llamando a [`sdata`](@ref). Para otros tipos de `AbstractArray`, `4d61726b646f776e2e436f64652822222c202273646174612229_40726566` simplemente devuelve el objeto en sí, por lo que es seguro usar `4d61726b646f776e2e436f64652822222c202273646174612229_40726566` en cualquier objeto de tipo `Array`.

El constructor para un array compartido tiene la forma:

```julia
SharedArray{T,N}(dims::NTuple; init=false, pids=Int[])
```

que crea un array compartido de `N` dimensiones de un tipo de bits `T` y tamaño `dims` a través de los procesos especificados por `pids`. A diferencia de los arrays distribuidos, un array compartido solo es accesible desde aquellos trabajadores participantes especificados por el argumento nombrado `pids` (y el proceso creador también, si está en el mismo host). Tenga en cuenta que solo se admiten elementos que son [`isbits`](@ref) en un SharedArray.

Si se especifica una función `init`, con la firma `initfn(S::SharedArray)`, se llama en todos los trabajadores participantes. Puedes especificar que cada trabajador ejecute la función `init` en una porción distinta del arreglo, lo que permite paralelizar la inicialización.

Aquí hay un breve ejemplo:

```julia-repl
julia> using Distributed

julia> addprocs(3)
3-element Array{Int64,1}:
 2
 3
 4

julia> @everywhere using SharedArrays

julia> S = SharedArray{Int,2}((3,4), init = S -> S[localindices(S)] = repeat([myid()], length(localindices(S))))
3×4 SharedArray{Int64,2}:
 2  2  3  4
 2  3  3  4
 2  3  4  4

julia> S[3,2] = 7
7

julia> S
3×4 SharedArray{Int64,2}:
 2  2  3  4
 2  3  3  4
 2  7  4  4
```

[`SharedArrays.localindices`](@ref) proporciona rangos de índices unidimensionales disjuntos, y a veces es conveniente para dividir tareas entre procesos. Puedes, por supuesto, dividir el trabajo de la manera que desees:

```julia-repl
julia> S = SharedArray{Int,2}((3,4), init = S -> S[indexpids(S):length(procs(S)):length(S)] = repeat([myid()], length( indexpids(S):length(procs(S)):length(S))))
3×4 SharedArray{Int64,2}:
 2  2  2  2
 3  3  3  3
 4  4  4  4
```

Dado que todos los procesos tienen acceso a los datos subyacentes, debes tener cuidado de no crear conflictos. Por ejemplo:

```julia
@sync begin
    for p in procs(S)
        @async begin
            remotecall_wait(fill!, p, S, p)
        end
    end
end
```

resultaría en un comportamiento indefinido. Debido a que cada proceso llena el *entero* arreglo con su propio `pid`, el proceso que se ejecute por último (para cualquier elemento particular de `S`) tendrá su `pid` retenido.

Como un ejemplo más extenso y complejo, considera ejecutar el siguiente "núcleo" en paralelo:

```julia
q[i,j,t+1] = q[i,j,t] + u[i,j,t]
```

En este caso, si intentamos dividir el trabajo utilizando un índice unidimensional, es probable que tengamos problemas: si `q[i,j,t]` está cerca del final del bloque asignado a un trabajador y `q[i,j,t+1]` está cerca del principio del bloque asignado a otro, es muy probable que `q[i,j,t]` no esté listo en el momento en que se necesita para calcular `q[i,j,t+1]`. En tales casos, es mejor dividir manualmente el arreglo. Vamos a dividir a lo largo de la segunda dimensión. Define una función que devuelva los índices `(irange, jrange)` asignados a este trabajador:

```julia-repl
julia> @everywhere function myrange(q::SharedArray)
           idx = indexpids(q)
           if idx == 0 # This worker is not assigned a piece
               return 1:0, 1:0
           end
           nchunks = length(procs(q))
           splits = [round(Int, s) for s in range(0, stop=size(q,2), length=nchunks+1)]
           1:size(q,1), splits[idx]+1:splits[idx+1]
       end
```

A continuación, define el núcleo:

```julia-repl
julia> @everywhere function advection_chunk!(q, u, irange, jrange, trange)
           @show (irange, jrange, trange)  # display so we can see what's happening
           for t in trange, j in jrange, i in irange
               q[i,j,t+1] = q[i,j,t] + u[i,j,t]
           end
           q
       end
```

También definimos un envoltorio de conveniencia para una implementación de `SharedArray`

```julia-repl
julia> @everywhere advection_shared_chunk!(q, u) =
           advection_chunk!(q, u, myrange(q)..., 1:size(q,3)-1)
```

Ahora comparemos tres versiones diferentes, una que se ejecuta en un solo proceso:

```julia-repl
julia> advection_serial!(q, u) = advection_chunk!(q, u, 1:size(q,1), 1:size(q,2), 1:size(q,3)-1);
```

uno que usa [`@distributed`](@ref):

```julia-repl
julia> function advection_parallel!(q, u)
           for t = 1:size(q,3)-1
               @sync @distributed for j = 1:size(q,2)
                   for i = 1:size(q,1)
                       q[i,j,t+1]= q[i,j,t] + u[i,j,t]
                   end
               end
           end
           q
       end;
```

y uno que delega en partes:

```julia-repl
julia> function advection_shared!(q, u)
           @sync begin
               for p in procs(q)
                   @async remotecall_wait(advection_shared_chunk!, p, q, u)
               end
           end
           q
       end;
```

Si creamos `SharedArray`s y cronometramos estas funciones, obtenemos los siguientes resultados (con `julia -p 4`):

```julia-repl
julia> q = SharedArray{Float64,3}((500,500,500));

julia> u = SharedArray{Float64,3}((500,500,500));
```

Ejecuta las funciones una vez para compilar JIT y [`@time`](@ref) en la segunda ejecución:

```julia-repl
julia> @time advection_serial!(q, u);
(irange,jrange,trange) = (1:500,1:500,1:499)
 830.220 milliseconds (216 allocations: 13820 bytes)

julia> @time advection_parallel!(q, u);
   2.495 seconds      (3999 k allocations: 289 MB, 2.09% gc time)

julia> @time advection_shared!(q,u);
        From worker 2:       (irange,jrange,trange) = (1:500,1:125,1:499)
        From worker 4:       (irange,jrange,trange) = (1:500,251:375,1:499)
        From worker 3:       (irange,jrange,trange) = (1:500,126:250,1:499)
        From worker 5:       (irange,jrange,trange) = (1:500,376:500,1:499)
 238.119 milliseconds (2264 allocations: 169 KB)
```

La mayor ventaja de `advection_shared!` es que minimiza el tráfico entre los trabajadores, lo que permite a cada uno calcular durante un tiempo prolongado en la parte asignada.

### Shared Arrays and Distributed Garbage Collection

Al igual que las referencias remotas, los arreglos compartidos también dependen de la recolección de basura en el nodo creador para liberar referencias de todos los trabajadores participantes. El código que crea muchos objetos de arreglo compartido de corta duración se beneficiaría de la finalización explícita de estos objetos lo antes posible. Esto resulta en que tanto la memoria como los manejadores de archivos que mapean el segmento compartido se liberen más pronto.

## ClusterManagers

El lanzamiento, la gestión y la conexión de procesos de Julia en un clúster lógico se realiza a través de administradores de clúster. Un `ClusterManager` es responsable de

  * lanzando procesos de trabajo en un entorno de clúster
  * gestionando eventos durante la vida útil de cada trabajador
  * opcionalmente, proporcionando transporte de datos

Un clúster de Julia tiene las siguientes características:

  * El proceso inicial de Julia, también llamado `master`, es especial y tiene un `id` de 1.
  * Solo el proceso `master` puede agregar o eliminar procesos de trabajo.
  * Todos los procesos pueden comunicarse directamente entre sí.

Las conexiones entre trabajadores (utilizando el transporte TCP/IP incorporado) se establecen de la siguiente manera:

  * [`addprocs`](@ref) se llama en el proceso maestro con un objeto `ClusterManager`.
  * [`addprocs`](@ref) llama el método apropiado [`launch`](@ref) que genera el número requerido de procesos de trabajo en las máquinas apropiadas.
  * Cada trabajador comienza a escuchar en un puerto libre y escribe su información de host y puerto en [`stdout`](@ref).
  * El administrador de clúster captura el [`stdout`](@ref) de cada trabajador y lo pone a disposición del proceso maestro.
  * El proceso maestro analiza esta información y establece conexiones TCP/IP con cada trabajador.
  * Cada trabajador también es notificado de otros trabajadores en el clúster.
  * Cada trabajador se conecta a todos los trabajadores cuyo `id` es menor que el `id` del propio trabajador.
  * De esta manera se establece una red de malla, en la que cada trabajador está directamente conectado con cada otro trabajador.

Mientras que la capa de transporte predeterminada utiliza [`TCPSocket`](@ref) en texto plano, es posible que un clúster de Julia proporcione su propio transporte.

Julia proporciona dos administradores de clúster integrados:

  * `LocalManager`, utilizado cuando se llaman [`addprocs()`](@ref) o [`addprocs(np::Integer)`](@ref)
  * `SSHManager`, utilizado cuando [`addprocs(hostnames::Array)`](@ref) es llamado con una lista de nombres de host.

`LocalManager` se utiliza para lanzar trabajadores adicionales en el mismo host, aprovechando así el hardware de múltiples núcleos y múltiples procesadores.

Así, un gestor de clústeres mínimo necesitaría:

  * ser un subtipo de la clase abstracta `ClusterManager`
  * implementar [`launch`](@ref), un método responsable de lanzar nuevos trabajadores
  * implementar [`manage`](@ref), que se llama en varios eventos durante la vida de un trabajador (por ejemplo, enviando una señal de interrupción)

[`addprocs(manager::FooManager)`](@ref addprocs) requiere que `FooManager` implemente:

```julia
function launch(manager::FooManager, params::Dict, launched::Array, c::Condition)
    [...]
end

function manage(manager::FooManager, id::Integer, config::WorkerConfig, op::Symbol)
    [...]
end
```

Como ejemplo, veamos cómo se implementa el `LocalManager`, el administrador responsable de iniciar trabajadores en el mismo host:

```julia
struct LocalManager <: ClusterManager
    np::Integer
end

function launch(manager::LocalManager, params::Dict, launched::Array, c::Condition)
    [...]
end

function manage(manager::LocalManager, id::Integer, config::WorkerConfig, op::Symbol)
    [...]
end
```

El método [`launch`](@ref) toma los siguientes argumentos:

  * `manager::ClusterManager`: el administrador de clúster que se llama con [`addprocs`](@ref)
  * `params::Dict`: todos los argumentos de palabra clave pasados a [`addprocs`](@ref)
  * `launched::Array`: el array al que se agregarán uno o más objetos `WorkerConfig`
  * `c::Condition`: la variable de condición que se notificará a medida que se lancen los trabajadores

El método [`launch`](@ref) se llama de manera asíncrona en una tarea separada. La finalización de esta tarea señala que todos los trabajadores solicitados han sido lanzados. Por lo tanto, la función `4d61726b646f776e2e436f64652822222c20226c61756e63682229_40726566` DEBE salir tan pronto como todos los trabajadores solicitados hayan sido lanzados.

Los trabajadores recién lanzados están conectados entre sí y al proceso maestro de manera total. Especificar el argumento de línea de comandos `--worker[=<cookie>]` resulta en que los procesos lanzados se inicialicen como trabajadores y se establezcan conexiones a través de sockets TCP/IP.

Todos los trabajadores en un clúster comparten el mismo [cookie](@ref man-cluster-cookie) que el maestro. Cuando la cookie no está especificada, es decir, con la opción `--worker`, el trabajador intenta leerla de su entrada estándar. `LocalManager` y `SSHManager` ambos pasan la cookie a los trabajadores recién lanzados a través de sus entradas estándar.

Por defecto, un trabajador escuchará en un puerto libre en la dirección devuelta por una llamada a [`getipaddr()`](@ref). Se puede especificar una dirección específica para escuchar mediante el argumento opcional `--bind-to bind_addr[:port]`. Esto es útil para hosts con múltiples direcciones.

Como ejemplo de un transporte que no es TCP/IP, una implementación puede optar por usar MPI, en cuyo caso `--worker` NO debe ser especificado. En su lugar, los trabajadores recién lanzados deben llamar a `init_worker(cookie)` antes de usar cualquiera de las construcciones paralelas.

Para cada trabajador lanzado, el método [`launch`](@ref) debe agregar un objeto `WorkerConfig` (con los campos apropiados inicializados) a `launched`

```julia
mutable struct WorkerConfig
    # Common fields relevant to all cluster managers
    io::Union{IO, Nothing}
    host::Union{AbstractString, Nothing}
    port::Union{Integer, Nothing}

    # Used when launching additional workers at a host
    count::Union{Int, Symbol, Nothing}
    exename::Union{AbstractString, Cmd, Nothing}
    exeflags::Union{Cmd, Nothing}

    # External cluster managers can use this to store information at a per-worker level
    # Can be a dict if multiple fields need to be stored.
    userdata::Any

    # SSHManager / SSH tunnel connections to workers
    tunnel::Union{Bool, Nothing}
    bind_addr::Union{AbstractString, Nothing}
    sshflags::Union{Cmd, Nothing}
    max_parallel::Union{Integer, Nothing}

    # Used by Local/SSH managers
    connect_at::Any

    [...]
end
```

La mayoría de los campos en `WorkerConfig` son utilizados por los administradores integrados. Los administradores de clúster personalizados normalmente especificarían solo `io` o `host` / `port`:

  * Si se especifica `io`, se utiliza para leer la información de host/puerto. Un trabajador de Julia imprime su dirección de enlace y puerto al inicio. Esto permite que los trabajadores de Julia escuchen en cualquier puerto libre disponible en lugar de requerir que los puertos de los trabajadores se configuren manualmente.
  * Si `io` no está especificado, se utilizan `host` y `port` para conectarse.
  * `count`, `exename` y `exeflags` son relevantes para lanzar trabajadores adicionales desde un trabajador. Por ejemplo, un administrador de clúster puede lanzar un solo trabajador por nodo y usarlo para lanzar trabajadores adicionales.

      * `count` con un valor entero `n` lanzará un total de `n` trabajadores.
      * `count` con un valor de `:auto` lanzará tantos trabajadores como el número de hilos de CPU (núcleos lógicos) en esa máquina.
      * `exename` es el nombre del ejecutable `julia`, incluyendo la ruta completa.
      * `exeflags` debe establecerse en los argumentos de línea de comandos requeridos para los nuevos trabajadores.
  * `tunnel`, `bind_addr`, `sshflags` y `max_parallel` se utilizan cuando se requiere un túnel ssh para conectarse a los trabajadores desde el proceso maestro.
  * `userdata` se proporciona para que los administradores de clústeres personalizados almacenen su propia información específica de los trabajadores.

`manage(manager::FooManager, id::Integer, config::WorkerConfig, op::Symbol)` se llama en diferentes momentos durante la vida del trabajador con valores `op` apropiados:

  * con `:register`/`:deregister` cuando un trabajador es agregado / eliminado del grupo de trabajadores de Julia.
  * con `:interrupt` cuando se llama a `interrupt(workers)`. El `ClusterManager` debe enviar la señal de interrupción apropiada al trabajador correspondiente.
  * con `:finalize` para propósitos de limpieza.

### Cluster Managers with Custom Transports

Reemplazar las conexiones de socket TCP/IP predeterminadas de todos a todos con una capa de transporte personalizada es un poco más complicado. Cada proceso de Julia tiene tantas tareas de comunicación como los trabajadores a los que está conectado. Por ejemplo, considera un clúster de Julia de 32 procesos en una red de malla de todos a todos:

  * Cada proceso de Julia tiene así 31 tareas de comunicación.
  * Cada tarea maneja todos los mensajes entrantes de un solo trabajador remoto en un bucle de procesamiento de mensajes.
  * El bucle de procesamiento de mensajes espera en un objeto `IO` (por ejemplo, un [`TCPSocket`](@ref) en la implementación predeterminada), lee un mensaje completo, lo procesa y espera el siguiente.
  * Enviar mensajes a un proceso se realiza directamente desde cualquier tarea de Julia, no solo desde tareas de comunicación, nuevamente, a través del objeto `IO` apropiado.

Reemplazar el transporte predeterminado requiere que la nueva implementación configure conexiones a trabajadores remotos y proporcione objetos `IO` apropiados en los que los bucles de procesamiento de mensajes puedan esperar. Los callbacks específicos del administrador que deben implementarse son:

```julia
connect(manager::FooManager, pid::Integer, config::WorkerConfig)
kill(manager::FooManager, pid::Int, config::WorkerConfig)
```

La implementación predeterminada (que utiliza sockets TCP/IP) se implementa como `connect(manager::ClusterManager, pid::Integer, config::WorkerConfig)`.

`connect` debe devolver un par de objetos `IO`, uno para leer datos enviados desde el trabajador `pid`, y el otro para escribir datos que necesitan ser enviados al trabajador `pid`. Los administradores de clúster personalizados pueden usar un `BufferStream` en memoria como el conducto para intermediar datos entre el transporte personalizado, posiblemente no `IO`, y la infraestructura paralela incorporada de Julia.

Un `BufferStream` es un [`IOBuffer`](@ref) que se comporta como un `IO`–es un flujo que se puede manejar de manera asíncrona.

La carpeta `clustermanager/0mq` en [Examples repository](https://github.com/JuliaAttic/Examples) contiene un ejemplo de uso de ZeroMQ para conectar trabajadores de Julia en una topología estelar con un corredor 0MQ en el medio. Nota: Los procesos de Julia siguen estando todos *lógicamente* conectados entre sí; cualquier trabajador puede enviar un mensaje a cualquier otro trabajador directamente sin tener conocimiento de que se está utilizando 0MQ como la capa de transporte.

Cuando se utilizan transportes personalizados:

  * Los trabajadores de Julia NO deben iniciarse con `--worker`. Comenzar con `--worker` resultará en que los nuevos trabajadores lanzados utilicen por defecto la implementación de transporte de socket TCP/IP.
  * Para cada conexión lógica entrante con un trabajador, se debe llamar a `Base.process_messages(rd::IO, wr::IO)()`. Esto inicia una nueva tarea que maneja la lectura y escritura de mensajes desde/hacia el trabajador representado por los objetos `IO`.
  * `init_worker(cookie, manager::FooManager)` *debe* ser llamado como parte de la inicialización del proceso del trabajador.
  * El campo `connect_at::Any` en `WorkerConfig` puede ser establecido por el administrador del clúster cuando se llama a [`launch`](@ref). El valor de este campo se pasa en todos los callbacks [`connect`](@ref). Típicamente, lleva información sobre *cómo conectarse* a un trabajador. Por ejemplo, el transporte de socket TCP/IP utiliza este campo para especificar la tupla `(host, port)` a la que conectarse a un trabajador.

`kill(manager, pid, config)` se llama para eliminar un trabajador del clúster. En el proceso maestro, los objetos `IO` correspondientes deben cerrarse por la implementación para garantizar una limpieza adecuada. La implementación predeterminada simplemente ejecuta una llamada a `exit()` en el trabajador remoto especificado.

La carpeta de Ejemplos `clustermanager/simple` es un ejemplo que muestra una implementación simple utilizando sockets de dominio UNIX para la configuración del clúster.

### Network Requirements for LocalManager and SSHManager

Los clústeres de Julia están diseñados para ejecutarse en entornos ya asegurados en infraestructuras como laptops locales, clústeres departamentales o incluso en la nube. Esta sección cubre los requisitos de seguridad de red para el `LocalManager` y `SSHManager` integrados:

  * El proceso maestro no escucha en ningún puerto. Solo se conecta a los trabajadores.
  * Cada trabajador se vincula a solo una de las interfaces locales y escucha en un número de puerto efímero asignado por el sistema operativo.
  * `LocalManager`, utilizado por `addprocs(N)`, por defecto solo se vincula a la interfaz de bucle invertido. Esto significa que los trabajadores iniciados más tarde en hosts remotos (o por cualquier persona con intenciones maliciosas) no pueden conectarse al clúster. Un `addprocs(4)` seguido de un `addprocs(["remote_host"])` fallará. Algunos usuarios pueden necesitar crear un clúster que comprenda su sistema local y algunos sistemas remotos. Esto se puede hacer solicitando explícitamente a `LocalManager` que se vincule a una interfaz de red externa a través del argumento de palabra clave `restrict`: `addprocs(4; restrict=false)`.
  * `SSHManager`, utilizado por `addprocs(list_of_remote_hosts)`, lanza trabajadores en hosts remotos a través de SSH. Por defecto, SSH solo se utiliza para lanzar trabajadores de Julia. Las conexiones posteriores entre el maestro y los trabajadores, así como entre los trabajadores, utilizan sockets TCP/IP sin cifrar. Los hosts remotos deben tener habilitada la entrada sin contraseña. Se pueden especificar banderas SSH adicionales o credenciales a través del argumento de palabra clave `sshflags`.
  * `addprocs(list_of_remote_hosts; tunnel=true, sshflags=<ssh keys and other flags>)` es útil cuando deseamos utilizar conexiones SSH para el maestro-trabajador también. Un escenario típico para esto es una laptop local ejecutando el REPL de Julia (es decir, el maestro) con el resto del clúster en la nube, digamos en Amazon EC2. En este caso, solo se necesita abrir el puerto 22 en el clúster remoto junto con un cliente SSH autenticado a través de infraestructura de clave pública (PKI). Las credenciales de autenticación se pueden proporcionar a través de `sshflags`, por ejemplo ```sshflags=`-i <keyfile>` ```.

    En una topología de todos a todos (la predeterminada), todos los trabajadores se conectan entre sí a través de sockets TCP simples. Por lo tanto, la política de seguridad en los nodos del clúster debe garantizar la conectividad libre entre los trabajadores para el rango de puertos efímeros (varía según el sistema operativo).

    Asegurar y encriptar todo el tráfico entre trabajadores (a través de SSH) o encriptar mensajes individuales se puede hacer a través de un `ClusterManager` personalizado.
  * Si especificas `multiplex=true` como una opción para [`addprocs`](@ref), se utiliza la multiplexión SSH para crear un túnel entre el maestro y los trabajadores. Si has configurado la multiplexión SSH por tu cuenta y la conexión ya se ha establecido, se utiliza la multiplexión SSH independientemente de la opción `multiplex`. Si la multiplexión está habilitada, el reenvío se establece utilizando la conexión existente (opción `-O forward` en ssh). Esto es beneficioso si tus servidores requieren autenticación por contraseña; puedes evitar la autenticación en Julia iniciando sesión en el servidor antes de `4d61726b646f776e2e436f64652822222c202261646470726f63732229_40726566`. El socket de control se ubicará en `~/.ssh/julia-%r@%h:%p` durante la sesión, a menos que se utilice la conexión de multiplexión existente. Ten en cuenta que el ancho de banda puede estar limitado si creas múltiples procesos en un nodo y habilitas la multiplexión, porque en ese caso los procesos comparten una única conexión TCP de multiplexión.

### [Cluster Cookie](@id man-cluster-cookie)

Todos los procesos en un clúster comparten la misma cookie que, por defecto, es una cadena generada aleatoriamente en el proceso maestro:

  * [`cluster_cookie()`](@ref) devuelve la cookie, mientras que `cluster_cookie(cookie)()` la establece y devuelve la nueva cookie.
  * Todas las conexiones están autenticadas en ambos lados para garantizar que solo los trabajadores iniciados por el maestro puedan conectarse entre sí.
  * La cookie puede ser pasada a los trabajadores al inicio a través del argumento `--worker=<cookie>`. Si se especifica el argumento `--worker` sin la cookie, el trabajador intenta leer la cookie de su entrada estándar ([`stdin`](@ref)). La `stdin` se cierra inmediatamente después de que se recupera la cookie.
  * Los `ClusterManager` pueden recuperar la cookie en el maestro llamando a [`cluster_cookie()`](@ref). Los administradores de clúster que no utilizan el transporte TCP/IP predeterminado (y por lo tanto no especifican `--worker`) deben llamar a `init_worker(cookie, manager)` con la misma cookie que en el maestro.

Tenga en cuenta que los entornos que requieren niveles más altos de seguridad pueden implementar esto a través de un `ClusterManager` personalizado. Por ejemplo, las cookies se pueden compartir previamente y, por lo tanto, no se especifican como un argumento de inicio.

## Specifying Network Topology (Experimental)

El argumento de palabra clave `topology` pasado a [`addprocs`](@ref) se utiliza para especificar cómo deben estar conectados los trabajadores entre sí:

  * `:all_to_all`, el predeterminado: todos los trabajadores están conectados entre sí.
  * `:master_worker`: solo el proceso del controlador, es decir, `pid` 1, tiene conexiones con los trabajadores.
  * `:custom`: el método `launch` del administrador de clúster especifica la topología de conexión a través de los campos `ident` y `connect_idents` en `WorkerConfig`. Un trabajador con una identidad `ident` proporcionada por el administrador de clúster se conectará a todos los trabajadores especificados en `connect_idents`.

El argumento de palabra clave `lazy=true|false` solo afecta a la opción `topology` `:all_to_all`. Si es `true`, el clúster comienza con el maestro conectado a todos los trabajadores. Las conexiones específicas entre trabajadores se establecen en la primera invocación remota entre dos trabajadores. Esto ayuda a reducir los recursos iniciales asignados para la comunicación intra-clúster. Las conexiones se configuran según los requisitos de tiempo de ejecución de un programa paralelo. El valor predeterminado para `lazy` es `true`.

Actualmente, enviar un mensaje entre trabajadores no conectados resulta en un error. Este comportamiento, al igual que la funcionalidad y la interfaz, debe considerarse experimental por naturaleza y puede cambiar en futuras versiones.

## Noteworthy external packages

Fuera del paralelismo de Julia, hay muchos paquetes externos que deberían mencionarse. Por ejemplo, [`MPI.jl`](https://github.com/JuliaParallel/MPI.jl) es un envoltorio de Julia para el protocolo `MPI`, [`Dagger.jl`](https://github.com/JuliaParallel/Dagger.jl) proporciona funcionalidad similar a [Dask](https://dask.org/) de Python, y [`DistributedArrays.jl`](https://github.com/JuliaParallel/Distributedarrays.jl) proporciona operaciones de arreglos distribuidas entre trabajadores, como [outlined above](@ref man-shared-arrays).

Se debe mencionar el ecosistema de programación en GPU de Julia, que incluye:

1. [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl) envuelve las diversas bibliotecas de CUDA y admite la compilación de núcleos de Julia para GPUs de Nvidia.
2. [oneAPI.jl](https://github.com/JuliaGPU/oneAPI.jl) envuelve el modelo de programación unificado oneAPI y admite la ejecución de núcleos de Julia en aceleradores compatibles. Actualmente, solo se admite Linux.
3. [AMDGPU.jl](https://github.com/JuliaGPU/AMDGPU.jl) envuelve las bibliotecas AMD ROCm y admite la compilación de núcleos de Julia para GPUs AMD. Actualmente, solo se admite Linux.
4. Bibliotecas de alto nivel como [KernelAbstractions.jl](https://github.com/JuliaGPU/KernelAbstractions.jl), [Tullio.jl](https://github.com/mcabbott/Tullio.jl) y [ArrayFire.jl](https://github.com/JuliaComputing/ArrayFire.jl).

En el siguiente ejemplo utilizaremos tanto `DistributedArrays.jl` como `CUDA.jl` para distribuir un arreglo a través de múltiples procesos, primero convirtiéndolo mediante `distribute()` y `CuArray()`.

Recuerda que al importar `DistributedArrays.jl` debes importarlo en todos los procesos usando [`@everywhere`](@ref)

```julia-repl
$ ./julia -p 4

julia> addprocs()

julia> @everywhere using DistributedArrays

julia> using CUDA

julia> B = ones(10_000) ./ 2;

julia> A = ones(10_000) .* π;

julia> C = 2 .* A ./ B;

julia> all(C .≈ 4*π)
true

julia> typeof(C)
Array{Float64,1}

julia> dB = distribute(B);

julia> dA = distribute(A);

julia> dC = 2 .* dA ./ dB;

julia> all(dC .≈ 4*π)
true

julia> typeof(dC)
DistributedArrays.DArray{Float64,1,Array{Float64,1}}

julia> cuB = CuArray(B);

julia> cuA = CuArray(A);

julia> cuC = 2 .* cuA ./ cuB;

julia> all(cuC .≈ 4*π);
true

julia> typeof(cuC)
CuArray{Float64,1}
```

En el siguiente ejemplo utilizaremos tanto `DistributedArrays.jl` como `CUDA.jl` para distribuir un arreglo a través de múltiples procesos y llamar a una función genérica sobre él.

```julia
function power_method(M, v)
    for i in 1:100
        v = M*v
        v /= norm(v)
    end

    return v, norm(M*v) / norm(v)  # or  (M*v) ./ v
end
```

`power_method` crea repetidamente un nuevo vector y lo normaliza. No hemos especificado ningún tipo de firma en la declaración de la función, veamos si funciona con los tipos de datos mencionados:

```julia-repl
julia> M = [2. 1; 1 1];

julia> v = rand(2)
2-element Array{Float64,1}:
0.40395
0.445877

julia> power_method(M,v)
([0.850651, 0.525731], 2.618033988749895)

julia> cuM = CuArray(M);

julia> cuv = CuArray(v);

julia> curesult = power_method(cuM, cuv);

julia> typeof(curesult)
CuArray{Float64,1}

julia> dM = distribute(M);

julia> dv = distribute(v);

julia> dC = power_method(dM, dv);

julia> typeof(dC)
Tuple{DistributedArrays.DArray{Float64,1,Array{Float64,1}},Float64}
```

Para finalizar esta breve exposición sobre paquetes externos, podemos considerar `MPI.jl`, un envoltorio de Julia del protocolo MPI. Como tomaría demasiado tiempo considerar cada función interna, sería mejor simplemente apreciar el enfoque utilizado para implementar el protocolo.

Considere este script de juguete que simplemente llama a cada subprocesso, instancia su rango y cuando se alcanza el proceso maestro, realiza la suma de los rangos.

```julia
import MPI

MPI.Init()

comm = MPI.COMM_WORLD
MPI.Barrier(comm)

root = 0
r = MPI.Comm_rank(comm)

sr = MPI.Reduce(r, MPI.SUM, root, comm)

if(MPI.Comm_rank(comm) == root)
   @printf("sum of ranks: %s\n", sr)
end

MPI.Finalize()
```

```
mpirun -np 4 ./julia example.jl
```

[^1]: In this context, MPI refers to the MPI-1 standard. Beginning with MPI-2, the MPI standards committee introduced a new set of communication mechanisms, collectively referred to as Remote Memory Access (RMA). The motivation for adding rma to the MPI standard was to facilitate one-sided communication patterns. For additional information on the latest MPI standard, see [https://mpi-forum.org/docs](https://mpi-forum.org/docs).
