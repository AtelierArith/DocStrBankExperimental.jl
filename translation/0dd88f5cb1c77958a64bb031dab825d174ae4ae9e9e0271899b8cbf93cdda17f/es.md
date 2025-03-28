# Profiling

El módulo `Profile` proporciona herramientas para ayudar a los desarrolladores a mejorar el rendimiento de su código. Cuando se utiliza, toma mediciones sobre el código en ejecución y produce una salida que te ayuda a entender cuánto tiempo se gasta en cada línea. El uso más común es identificar "cuellos de botella" como objetivos para la optimización.

`Perfil` implementa lo que se conoce como un "muestreo" o [statistical profiler](https://en.wikipedia.org/wiki/Profiling_(computer_programming)). Funciona tomando periódicamente un backtrace durante la ejecución de cualquier tarea. Cada backtrace captura la función que se está ejecutando actualmente y el número de línea, además de la cadena completa de llamadas a funciones que llevaron a esta línea, y por lo tanto es una "instantánea" del estado actual de ejecución.

Si gran parte de tu tiempo de ejecución se gasta en ejecutar una línea de código particular, esta línea aparecerá con frecuencia en el conjunto de todas las trazas de pila. En otras palabras, el "costo" de una línea dada, o realmente, el costo de la secuencia de llamadas a funciones hasta e incluyendo esta línea, es proporcional a la frecuencia con la que aparece en el conjunto de todas las trazas de pila.

Un perfilador de muestreo no proporciona una cobertura completa línea por línea, porque las trazas de retorno ocurren en intervalos (por defecto, 1 ms en sistemas Unix y 10 ms en Windows, aunque la programación real está sujeta a la carga del sistema operativo). Además, como se discutirá más adelante, debido a que las muestras se recogen en un subconjunto escaso de todos los puntos de ejecución, los datos recopilados por un perfilador de muestreo están sujetos a ruido estadístico.

A pesar de estas limitaciones, los perfiles de muestreo tienen fortalezas sustanciales:

  * No tienes que hacer ninguna modificación a tu código para tomar mediciones de tiempo.
  * Puede perfilar en el código base de Julia e incluso (opcionalmente) en bibliotecas de C y Fortran.
  * Al ejecutar "infrecuentemente" hay muy poco sobrecarga de rendimiento; mientras se perfila, tu código puede ejecutarse a casi velocidad nativa.

Por estas razones, se recomienda que intentes usar el perfilador de muestreo integrado antes de considerar cualquier alternativa.

## Basic usage

Vamos a trabajar con un caso de prueba simple:

```julia-repl
julia> function myfunc()
           A = rand(200, 200, 400)
           maximum(A)
       end
```

Es una buena idea ejecutar primero el código que planeas perfilar al menos una vez (a menos que quieras perfilar el compilador JIT de Julia):

```julia-repl
julia> myfunc() # run once to force compilation
```

Ahora estamos listos para perfilar esta función:

```julia-repl
julia> using Profile

julia> @profile myfunc()
```

Para ver los resultados de perfilado, hay varios navegadores gráficos. Una "familia" de visualizadores se basa en [FlameGraphs.jl](https://github.com/timholy/FlameGraphs.jl), con cada miembro de la familia proporcionando una interfaz de usuario diferente:

  * [VS Code](https://www.julia-vscode.org/) es un IDE completo con soporte integrado para la visualización de perfiles.
  * [ProfileView.jl](https://github.com/timholy/ProfileView.jl) es un visualizador independiente basado en GTK.
  * [ProfileVega.jl](https://github.com/davidanthoff/ProfileVega.jl) utiliza VegaLight e integra bien con los cuadernos de Jupyter.
  * [StatProfilerHTML.jl](https://github.com/tkluck/StatProfilerHTML.jl) produce HTML y presenta algunos resúmenes adicionales, y también se integra bien con los cuadernos Jupyter.
  * [ProfileSVG.jl](https://github.com/timholy/ProfileSVG.jl) renderiza SVG
  * [PProf.jl](https://github.com/JuliaPerf/PProf.jl) sirve un sitio web local para inspeccionar gráficos, flamegraphs y más.
  * [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl) es una interfaz de visualización de perfil basada en HTML canvas, utilizada por el [Julia VS Code extension](https://www.julia-vscode.org/), pero también puede generar archivos HTML interactivos.

Un enfoque completamente independiente para la visualización de perfiles es [PProf.jl](https://github.com/vchuravy/PProf.jl), que utiliza la herramienta externa `pprof`.

Aquí, sin embargo, utilizaremos la visualización basada en texto que viene con la biblioteca estándar:

```julia-repl
julia> Profile.print()
80 ./event.jl:73; (::Base.REPL.##1#2{Base.REPL.REPLBackend})()
 80 ./REPL.jl:97; macro expansion
  80 ./REPL.jl:66; eval_user_input(::Any, ::Base.REPL.REPLBackend)
   80 ./boot.jl:235; eval(::Module, ::Any)
    80 ./<missing>:?; anonymous
     80 ./profile.jl:23; macro expansion
      52 ./REPL[1]:2; myfunc()
       38 ./random.jl:431; rand!(::MersenneTwister, ::Array{Float64,3}, ::Int64, ::Type{B...
        38 ./dSFMT.jl:84; dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_state, ::Ptr{F...
       14 ./random.jl:278; rand
        14 ./random.jl:277; rand
         14 ./random.jl:366; rand
          14 ./random.jl:369; rand
      28 ./REPL[1]:3; myfunc()
       28 ./reduce.jl:270; _mapreduce(::Base.#identity, ::Base.#scalarmax, ::IndexLinear,...
        3  ./reduce.jl:426; mapreduce_impl(::Base.#identity, ::Base.#scalarmax, ::Array{F...
        25 ./reduce.jl:428; mapreduce_impl(::Base.#identity, ::Base.#scalarmax, ::Array{F...
```

Cada línea de esta visualización representa un lugar particular (número de línea) en el código. La indentación se utiliza para indicar la secuencia anidada de llamadas a funciones, siendo las líneas más indentadas más profundas en la secuencia de llamadas. En cada línea, el primer "campo" es el número de trazas de retorno (muestras) tomadas *en esta línea o en cualquier función ejecutada por esta línea*. El segundo campo es el nombre del archivo y el número de línea, y el tercer campo es el nombre de la función. Ten en cuenta que los números de línea específicos pueden cambiar a medida que cambia el código de Julia; si deseas seguirlo, es mejor ejecutar este ejemplo tú mismo.

En este ejemplo, podemos ver que la función de nivel superior llamada está en el archivo `event.jl`. Esta es la función que ejecuta el REPL cuando inicias Julia. Si examinas la línea 97 de `REPL.jl`, verás que aquí es donde se llama a la función `eval_user_input()`. Esta es la función que evalúa lo que escribes en el REPL, y dado que estamos trabajando de manera interactiva, estas funciones se invocaron cuando ingresamos `@profile myfunc()`. La siguiente línea refleja las acciones tomadas en el macro [`@profile`](@ref).

La primera línea muestra que se tomaron 80 trazas de retroceso en la línea 73 de `event.jl`, pero no es que esta línea fuera "costosa" por sí sola: la tercera línea revela que todas estas 80 trazas de retroceso fueron en realidad desencadenadas dentro de su llamada a `eval_user_input`, y así sucesivamente. Para averiguar qué operaciones están realmente consumiendo tiempo, necesitamos mirar más a fondo en la cadena de llamadas.

La primera línea "importante" en esta salida es esta:

```
52 ./REPL[1]:2; myfunc()
```

`REPL` se refiere al hecho de que definimos `myfunc` en el REPL, en lugar de ponerlo en un archivo; si hubiéramos usado un archivo, esto mostraría el nombre del archivo. El `[1]` muestra que la función `myfunc` fue la primera expresión evaluada en esta sesión de REPL. La línea 2 de `myfunc()` contiene la llamada a `rand`, y hubo 52 (de 80) trazas de retroceso que ocurrieron en esta línea. Debajo de eso, puedes ver una llamada a `dsfmt_fill_array_close_open!` dentro de `dSFMT.jl`.

Un poco más abajo, ves:

```
28 ./REPL[1]:3; myfunc()
```

La línea 3 de `myfunc` contiene la llamada a `maximum`, y se tomaron 28 (de 80) trazas de retroceso aquí. Debajo, puedes ver los lugares específicos en `base/reduce.jl` que llevan a cabo las operaciones que consumen tiempo en la función `maximum` para este tipo de datos de entrada.

En general, podemos concluir tentativamente que generar los números aleatorios es aproximadamente el doble de costoso que encontrar el elemento máximo. Podríamos aumentar nuestra confianza en este resultado al recopilar más muestras:

```julia-repl
julia> @profile (for i = 1:100; myfunc(); end)

julia> Profile.print()
[....]
 3821 ./REPL[1]:2; myfunc()
  3511 ./random.jl:431; rand!(::MersenneTwister, ::Array{Float64,3}, ::Int64, ::Type...
   3511 ./dSFMT.jl:84; dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_state, ::Ptr...
  310  ./random.jl:278; rand
   [....]
 2893 ./REPL[1]:3; myfunc()
  2893 ./reduce.jl:270; _mapreduce(::Base.#identity, ::Base.#scalarmax, ::IndexLinea...
   [....]
```

En general, si tienes `N` muestras recolectadas en una línea, puedes esperar una incertidumbre del orden de `sqrt(N)` (salvo otras fuentes de ruido, como cuán ocupado está el ordenador con otras tareas). La principal excepción a esta regla es la recolección de basura, que se ejecuta con poca frecuencia pero tiende a ser bastante costosa. (Dado que el recolector de basura de Julia está escrito en C, tales eventos se pueden detectar utilizando el modo de salida `C=true` descrito a continuación, o utilizando [ProfileView.jl](https://github.com/timholy/ProfileView.jl).)

Esto ilustra el volcado "árbol" predeterminado; una alternativa es el volcado "plano", que acumula conteos independientemente de su anidamiento:

```julia-repl
julia> Profile.print(format=:flat)
 Count File          Line Function
  6714 ./<missing>     -1 anonymous
  6714 ./REPL.jl       66 eval_user_input(::Any, ::Base.REPL.REPLBackend)
  6714 ./REPL.jl       97 macro expansion
  3821 ./REPL[1]        2 myfunc()
  2893 ./REPL[1]        3 myfunc()
  6714 ./REPL[7]        1 macro expansion
  6714 ./boot.jl      235 eval(::Module, ::Any)
  3511 ./dSFMT.jl      84 dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_s...
  6714 ./event.jl      73 (::Base.REPL.##1#2{Base.REPL.REPLBackend})()
  6714 ./profile.jl    23 macro expansion
  3511 ./random.jl    431 rand!(::MersenneTwister, ::Array{Float64,3}, ::In...
   310 ./random.jl    277 rand
   310 ./random.jl    278 rand
   310 ./random.jl    366 rand
   310 ./random.jl    369 rand
  2893 ./reduce.jl    270 _mapreduce(::Base.#identity, ::Base.#scalarmax, :...
     5 ./reduce.jl    420 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
   253 ./reduce.jl    426 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
  2592 ./reduce.jl    428 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
    43 ./reduce.jl    429 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
```

Si tu código tiene recursión, un punto que puede resultar confuso es que una línea en una función "hija" puede acumular más conteos de los que hay en total de retrocesos. Considera las siguientes definiciones de funciones:

```julia
dumbsum(n::Integer) = n == 1 ? 1 : 1 + dumbsum(n-1)
dumbsum3() = dumbsum(3)
```

Si tuvieras que perfilar `dumbsum3`, y se tomara un backtrace mientras se estaba ejecutando `dumbsum(1)`, el backtrace se vería así:

```julia
dumbsum3
    dumbsum(3)
        dumbsum(2)
            dumbsum(1)
```

En consecuencia, esta función hija obtiene 3 conteos, aunque el padre solo obtiene uno. La representación en "árbol" hace que esto sea mucho más claro, y por esta razón (entre otras) es probablemente la forma más útil de ver los resultados.

## Accumulation and clearing

Los resultados de [`@profile`](@ref) se acumulan en un búfer; si ejecutas múltiples fragmentos de código bajo `4d61726b646f776e2e436f64652822222c20224070726f66696c652229_40726566`, entonces [`Profile.print()`](@ref) te mostrará los resultados combinados. Esto puede ser muy útil, pero a veces quieres empezar de nuevo; puedes hacerlo con [`Profile.clear()`](@ref).

## Options for controlling the display of profile results

[`Profile.print`](@ref) tiene más opciones de las que hemos descrito hasta ahora. Veamos la declaración completa:

```julia
function print(io::IO = stdout, data = fetch(); kwargs...)
```

Primero discutamos los dos argumentos posicionales y luego los argumentos de palabra clave:

  * `io` – Te permite guardar los resultados en un búfer, por ejemplo, un archivo, pero el valor predeterminado es imprimir en `stdout` (la consola).
  * `data` – Contiene los datos que deseas analizar; por defecto, eso se obtiene de [`Profile.fetch()`](@ref), que extrae las trazas de retroceso de un búfer preasignado. Por ejemplo, si deseas perfilar el perfilador, podrías decir:

    ```julia
    data = copy(Profile.fetch())
    Profile.clear()
    @profile Profile.print(stdout, data) # Prints the previous results
    Profile.print()                      # Prints results from Profile.print()
    ```

Los argumentos de palabra clave pueden ser cualquier combinación de:

  * `format` – Introducido anteriormente, determina si las trazas de pila se imprimen con (por defecto, `:tree`) o sin (`:flat`) sangrías que indican la estructura del árbol.
  * `C` – Si `true`, se muestran las trazas de retroceso desde el código C y Fortran (normalmente están excluidas). Intenta ejecutar el ejemplo introductorio con `Profile.print(C = true)`. Esto puede ser extremadamente útil para decidir si es el código de Julia o el código C el que está causando un cuello de botella; establecer `C = true` también mejora la interpretabilidad de la anidación, a costa de volcar perfiles más largos.
  * `combine` – Algunas líneas de código contienen múltiples operaciones; por ejemplo, `s += A[i]` contiene tanto una referencia de matriz (`A[i]`) como una operación de suma. Estas corresponden a diferentes líneas en el código máquina generado, y por lo tanto puede haber dos o más direcciones diferentes capturadas durante las trazas de retroceso en esta línea. `combine = true` las agrupa, y probablemente es lo que normalmente deseas, pero puedes generar una salida por separado para cada puntero de instrucción único con `combine = false`.
  * `maxdepth` – Limita los marcos a una profundidad superior a `maxdepth` en el formato `:tree`.
  * `sortedby` – Controla el orden en el formato `:flat`. `:filefuncline` (por defecto) ordena por la línea de origen, mientras que `:count` ordena en función del número de muestras recopiladas.
  * `noisefloor` – Limita los marcos que están por debajo del umbral de ruido heurístico de la muestra (solo se aplica al formato `:tree`). Un valor sugerido para probar esto es 2.0 (el valor predeterminado es 0). Este parámetro oculta muestras para las cuales `n <= noisefloor * √N`, donde `n` es el número de muestras en esta línea, y `N` es el número de muestras para el llamador.
  * `mincount` – Limita los marcos con menos de `mincount` ocurrencias.

Los nombres de archivos/funciones a veces se truncaron (con `...`), y la indentación se trunca con un `+n` al principio, donde `n` es el número de espacios adicionales que se habrían insertado, si hubiera habido espacio. Si deseas un perfil completo de código profundamente anidado, a menudo una buena idea es guardar en un archivo utilizando un `displaysize` amplio en un [`IOContext`](@ref):

```julia
open("/tmp/prof.txt", "w") do s
    Profile.print(IOContext(s, :displaysize => (24, 500)))
end
```

## Configuration

[`@profile`](@ref) solo acumula trazas de retroceso, y el análisis ocurre cuando llamas a [`Profile.print()`](@ref). Para un cálculo de larga duración, es completamente posible que el búfer preasignado para almacenar trazas de retroceso se llene. Si eso sucede, las trazas de retroceso se detienen, pero tu cálculo continúa. Como consecuencia, puedes perder algunos datos importantes de perfilado (recibirás una advertencia cuando eso suceda).

Puedes obtener y configurar los parámetros relevantes de esta manera:

```julia
Profile.init() # returns the current settings
Profile.init(n = 10^7, delay = 0.01)
```

`n` es el número total de punteros de instrucción que puedes almacenar, con un valor predeterminado de `10^6`. Si tu traza de retroceso típica es de 20 punteros de instrucción, entonces puedes recopilar 50000 trazas de retroceso, lo que sugiere una incertidumbre estadística de menos del 1%. Esto puede ser suficiente para la mayoría de las aplicaciones.

En consecuencia, es más probable que necesites modificar `delay`, expresado en segundos, que establece la cantidad de tiempo que Julia tiene entre instantáneas para realizar los cálculos solicitados. Un trabajo que se ejecute durante mucho tiempo podría no necesitar backtraces frecuentes. La configuración predeterminada es `delay = 0.001`. Por supuesto, puedes disminuir el retraso así como aumentarlo; sin embargo, la sobrecarga de la profilación crece una vez que el retraso se vuelve similar a la cantidad de tiempo necesario para tomar un backtrace (~30 microsegundos en la laptop del autor).

## Memory allocation analysis

Una de las técnicas más comunes para mejorar el rendimiento es reducir la asignación de memoria. Julia proporciona varias herramientas para medir esto:

### `@time`

La cantidad total de asignación se puede medir con [`@time`](@ref), [`@allocated`](@ref) y [`@allocations`](@ref), y las líneas específicas que desencadenan la asignación a menudo se pueden inferir a partir del perfilado a través del costo de la recolección de basura que estas líneas incurren. Sin embargo, a veces es más eficiente medir directamente la cantidad de memoria asignada por cada línea de código.

### GC Logging

Mientras [`@time`](@ref) registra estadísticas de alto nivel sobre el uso de memoria y la recolección de basura durante la evaluación de una expresión, puede ser útil registrar cada evento de recolección de basura, para tener una idea intuitiva de con qué frecuencia se ejecuta el recolector de basura, cuánto tiempo se ejecuta cada vez y cuánta basura recoge cada vez. Esto se puede habilitar con [`GC.enable_logging(true)`](@ref), lo que hace que Julia registre en stderr cada vez que ocurre una recolección de basura.

### [Allocation Profiler](@id allocation-profiler)

!!! compat "Julia 1.8"
    Esta funcionalidad requiere al menos Julia 1.8.


El perfilador de asignaciones registra la traza de pila, el tipo y el tamaño de cada asignación mientras se está ejecutando. Se puede invocar con [`Profile.Allocs.@profile`](@ref).

Esta información sobre las asignaciones se devuelve como un array de objetos `Alloc`, envueltos en un objeto `AllocResults`. La mejor manera de visualizar esto actualmente es con los paquetes [PProf.jl](https://github.com/JuliaPerf/PProf.jl) y [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl), que pueden visualizar las pilas de llamadas que están realizando la mayoría de las asignaciones.

El perfilador de asignación tiene una sobrecarga significativa, por lo que se puede pasar un argumento `sample_rate` para acelerarlo al hacer que omita algunas asignaciones. Pasar `sample_rate=1.0` hará que registre todo (lo cual es lento); `sample_rate=0.1` registrará solo el 10% de las asignaciones (más rápido), etc.

!!! compat "Julia 1.11"
    Las versiones anteriores de Julia no podían capturar tipos en todos los casos. En versiones anteriores de Julia, si ves una asignación del tipo `Profile.Allocs.UnknownType`, significa que el perfilador no sabe qué tipo de objeto fue asignado. Esto sucedió principalmente cuando la asignación provenía de código generado producido por el compilador. Consulta [issue #43688](https://github.com/JuliaLang/julia/issues/43688) para más información.

    Desde Julia 1.11, todas las asignaciones deben tener un tipo reportado.


Para más detalles sobre cómo usar esta herramienta, consulte la siguiente charla de JuliaCon 2022: https://www.youtube.com/watch?v=BFvpwC8hEWQ

##### Allocation Profiler Example

En este ejemplo simple, usamos PProf para visualizar el perfil de asignación. Podrías usar otra herramienta de visualización en su lugar. Recopilamos el perfil (especificando una tasa de muestreo), luego lo visualizamos.

```julia
using Profile, PProf
Profile.Allocs.clear()
Profile.Allocs.@profile sample_rate=0.0001 my_function()
PProf.Allocs.pprof()
```

Aquí hay un ejemplo más detallado, que muestra cómo podemos ajustar la tasa de muestreo. Un buen número de muestras a las que aspirar es de alrededor de 1 a 10 mil. Demasiadas, y el visualizador de perfiles puede verse abrumado, y el perfilado será lento. Muy pocas, y no tendrás una muestra representativa.

```julia-repl
julia> import Profile

julia> @time my_function()  # Estimate allocations from a (second-run) of the function
  0.110018 seconds (1.50 M allocations: 58.725 MiB, 17.17% gc time)
500000

julia> Profile.Allocs.clear()

julia> Profile.Allocs.@profile sample_rate=0.001 begin   # 1.5 M * 0.001 = ~1.5K allocs.
           my_function()
       end
500000

julia> prof = Profile.Allocs.fetch();  # If you want, you can also manually inspect the results.

julia> length(prof.allocs)  # Confirm we have expected number of allocations.
1515

julia> using PProf  # Now, visualize with an external tool, like PProf or ProfileCanvas.

julia> PProf.Allocs.pprof(prof; from_c=false)  # You can optionally pass in a previously fetched profile result.
Analyzing 1515 allocation samples... 100%|████████████████████████████████| Time: 0:00:00
Main binary filename not available.
Serving web UI on http://localhost:62261
"alloc-profile.pb.gz"
```

Luego puedes ver el perfil navegando a http://localhost:62261, y el perfil se guarda en el disco. Consulta el paquete PProf para más opciones.

##### Allocation Profiling Tips

Como se indicó anteriormente, apunte a alrededor de 1-10 mil muestras en su perfil.

Tenga en cuenta que estamos muestreando uniformemente en el espacio de *todas las asignaciones*, y no estamos ponderando nuestras muestras por el tamaño de la asignación. Por lo tanto, un perfil de asignación dado puede no ofrecer un perfil representativo de dónde se asignan la mayoría de los bytes en su programa, a menos que haya establecido `sample_rate=1`.

Las asignaciones pueden provenir de usuarios que construyen objetos directamente, pero también pueden provenir del interior del tiempo de ejecución o ser insertadas en código compilado para manejar la inestabilidad de tipos. Mirar la vista de "código fuente" puede ser útil para aislarlas, y luego otras herramientas externas como [`Cthulhu.jl`](https://github.com/JuliaDebug/Cthulhu.jl) pueden ser útiles para identificar la causa de la asignación.

##### Allocation Profile Visualization Tools

Hay varias herramientas de visualización de perfiles ahora que pueden mostrar Perfiles de Asignación. Aquí hay una pequeña lista de algunas de las principales que conocemos:

  * [PProf.jl](https://github.com/JuliaPerf/PProf.jl)
  * [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl)
  * El visualizador de perfiles integrado de VSCode (`@profview_allocs`) [se necesitan documentos]
  * Ver los resultados directamente en el REPL

      * Puedes inspeccionar los resultados en el REPL a través de [`Profile.Allocs.fetch()`](@ref), para ver el stacktrace y el tipo de cada asignación.

#### Line-by-Line Allocation Tracking

Una forma alternativa de medir las asignaciones es iniciar Julia con la opción de línea de comandos `--track-allocation=<configuración>`, para la cual puedes elegir `none` (el valor predeterminado, no medir la asignación), `user` (medir la asignación de memoria en todas partes excepto en el código central de Julia) o `all` (medir la asignación de memoria en cada línea de código de Julia). La asignación se mide para cada línea de código compilado. Cuando sales de Julia, los resultados acumulativos se escriben en archivos de texto con `.mem` añadido después del nombre del archivo, residiendo en el mismo directorio que el archivo fuente. Cada línea lista el número total de bytes asignados. El [`Coverage` package](https://github.com/JuliaCI/Coverage.jl) contiene algunas herramientas de análisis elementales, por ejemplo, para ordenar las líneas en orden de número de bytes asignados.

Al interpretar los resultados, hay algunos detalles importantes. Bajo la configuración `user`, la primera línea de cualquier función llamada directamente desde el REPL mostrará asignación debido a eventos que ocurren en el código del REPL mismo. Más significativamente, la compilación JIT también suma a los conteos de asignación, porque gran parte del compilador de Julia está escrito en Julia (y la compilación generalmente requiere asignación de memoria). El procedimiento recomendado es forzar la compilación ejecutando todos los comandos que deseas analizar, luego llama a [`Profile.clear_malloc_data()`](@ref) para restablecer todos los contadores de asignación. Finalmente, ejecuta los comandos deseados y cierra Julia para activar la generación de los archivos `.mem`.

!!! note
    `--track-allocation` cambia la generación de código para registrar las asignaciones, por lo que las asignaciones pueden ser diferentes a lo que ocurre sin la opción. Recomendamos usar el [allocation profiler](@ref allocation-profiler) en su lugar.


## External Profiling

Actualmente, Julia admite `Intel VTune`, `OProfile` y `perf` como herramientas de perfilado externas.

Dependiendo de la herramienta que elijas, compila con `USE_INTEL_JITEVENTS`, `USE_OPROFILE_JITEVENTS` y `USE_PERF_JITEVENTS` configurados en 1 en `Make.user`. Se admiten múltiples banderas.

Antes de ejecutar Julia, establece la variable de entorno [`ENABLE_JITPROFILING`](@ref ENABLE_JITPROFILING) en 1.

¡Ahora tienes una multitud de formas de emplear esas herramientas! Por ejemplo, con `OProfile` puedes intentar una grabación simple:

```
>ENABLE_JITPROFILING=1 sudo operf -Vdebug ./julia test/fastmath.jl
>opreport -l `which ./julia`
```

O de manera similar con `perf`:

```
$ ENABLE_JITPROFILING=1 perf record -o /tmp/perf.data --call-graph dwarf -k 1 ./julia /test/fastmath.jl
$ perf inject --jit --input /tmp/perf.data --output /tmp/perf-jit.data
$ perf report --call-graph -G -i /tmp/perf-jit.data
```

Hay muchas más cosas interesantes que puedes medir sobre tu programa. Para obtener una lista completa, por favor lee el [Linux perf examples page](https://www.brendangregg.com/perf.html).

Recuerda que `perf` guarda un archivo `perf.data` para cada ejecución que, incluso para programas pequeños, puede volverse bastante grande. Además, el módulo LLVM de perf guarda temporalmente objetos de depuración en `~/.debug/jit`, recuerda limpiar esa carpeta con frecuencia.
