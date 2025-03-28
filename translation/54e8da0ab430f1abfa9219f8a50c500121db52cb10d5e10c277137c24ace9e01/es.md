```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/NEWS.md"
```

# Julia v1.11 Release Notes

## New language features

  * New `Memory` type that provides a lower-level container as an alternative to `Array`. `Memory` has less overhead and a faster constructor, making it a good choice for situations that do not need all the features of `Array` (e.g. multiple dimensions). Most of the `Array` type is now implemented in Julia on top of `Memory`, leading to significant speedups for several functions (e.g. `push!`) as well as more maintainable code ([#51319](https://github.com/JuliaLang/julia/issues/51319)).
  * `public` is a new keyword. Symbols marked with `public` are considered public API. Symbols marked with `export` are now also treated as public API. The difference between `public` and `export` is that `public` names do not become available when `using` a package/module ([#50105](https://github.com/JuliaLang/julia/issues/50105)).
  * `ScopedValue` implementa el alcance dinámico con herencia a través de tareas ([#50958](https://github.com/JuliaLang/julia/issues/50958)).
  * Los archivos `Manifest.toml` ahora se pueden renombrar en el formato `Manifest-v{mayor}.{menor}.toml` para ser preferentemente utilizados por la versión de julia dada. Es decir, en la misma carpeta, un `Manifest-v1.11.toml` sería utilizado por v1.11 y `Manifest.toml` por cualquier otra versión de julia. Esto facilita la gestión de entornos para múltiples versiones de julia al mismo tiempo ([#43845](https://github.com/JuliaLang/julia/issues/43845)).
  * Soporte para Unicode 15.1 ([#51799](https://github.com/JuliaLang/julia/issues/51799)).

## Language changes

  * Durante la precompilación, los ganchos `atexit` ahora se ejecutan antes de guardar el archivo de salida. Esto permite a los usuarios desmantelar de manera segura el estado en segundo plano (como cerrar `Timer`s y enviar notificaciones de desconexión a tareas de latido) y limpiar otros recursos cuando el programa desea comenzar a salir.
  * La cobertura de código y el seguimiento de malloc ya no se generan durante la etapa de precompilación del paquete. Además, durante estos modos, ahora se utilizan cachés de pkgimage para paquetes que no están siendo rastreados. Esto significa que las pruebas de cobertura (el valor predeterminado para `julia-actions/julia-runtest`) utilizarán por defecto cachés de pkgimage para todos los demás paquetes que no sean el paquete que se está probando, lo que probablemente significa una ejecución de pruebas más rápida ([#52123](https://github.com/JuliaLang/julia/issues/52123)).
  * Especificar una ruta en `JULIA_DEPOT_PATH` ahora resulta en la expansión de cadenas vacías para omitir el depósito de usuario predeterminado ([#51448](https://github.com/JuliaLang/julia/issues/51448)).
  * Los archivos de caché de precompilación ahora son reubicables y su validez se verifica a través de un hash de contenido de sus archivos fuente en lugar de su `mtime` ([#49866](https://github.com/JuliaLang/julia/issues/49866)).
  * Las extensiones ahora pueden depender de otras extensiones, si sus activadores incluyen todos los activadores de cualquier extensión de la que deseen depender (+ al menos un activador adicional). Las dependencias de ext-a-ext que no cumplan con este requisito ahora están bloqueadas para usar `Base.get_extension` durante la precompilación, para prevenir ciclos de extensión [#55557](https://github.com/JuliaLang/julia/issues/55557).

## Compiler/Runtime improvements

  * Actualizadas las heurísticas de GC para contar las páginas asignadas en lugar de objetos individuales ([#50144](https://github.com/JuliaLang/julia/issues/50144)).
  * Se agregó soporte para anotar `Base.@assume_effects` en bloques de código ([#52400](https://github.com/JuliaLang/julia/issues/52400)).

## Command-line option changes

  * El punto de entrada para Julia se ha estandarizado a `Main.main(args)`. Esto debe ser explícitamente optado utilizando el macro `@main` (ver la documentación para más detalles). Cuando se opta, y `julia` se invoca para ejecutar un script o expresión (es decir, usando `julia script.jl` o `julia -e expr`), `julia` ejecutará automáticamente la función `Main.main`. Esto está destinado a unificar los flujos de trabajo de scripts y compilación, donde la carga de código puede ocurrir en el compilador y la ejecución de `Main.main` puede ocurrir en el ejecutable resultante. Para uso interactivo, no hay diferencia semántica entre definir una función `main` y ejecutar el código directamente al final del script ([#50974](https://github.com/JuliaLang/julia/issues/50974)).
  * Las opciones `--compiled-modules` y `--pkgimages` ahora se pueden establecer en `existing`, lo que hará que Julia considere cargar archivos de caché existentes, pero no crear nuevos ([#50586](https://github.com/JuliaLang/julia/issues/50586), [#52573](https://github.com/JuliaLang/julia/issues/52573)).
  * El argumento `--project` ahora acepta `@script` para dar una ruta a un directorio con un Project.toml relativo al archivo de script pasado. `--project=@script/foo` para el subdirectorio `foo`. Si no se da ninguna ruta después (es decir, `--project=@script`), entonces (como `--project=@.`) se busca en el directorio y sus padres un Project.toml ([#50864](https://github.com/JuliaLang/julia/issues/50864) y [#53352](https://github.com/JuliaLang/julia/issues/53352))

## Multi-threading changes

  * `Threads.@threads` ahora soporta el programador `:greedy`, destinado a cargas de trabajo no uniformes ([#52096](https://github.com/JuliaLang/julia/issues/52096)).
  * A new public (but unexported) struct `Base.Lockable{T, L<:AbstractLock}` makes it easy to bundle a resource and its lock together ([#52898](https://github.com/JuliaLang/julia/issues/52898)).

## Build system changes

  * Hay un nuevo `Makefile` para construir Julia y LLVM utilizando las estrategias de optimización guiada por perfil y optimizaciones en tiempo de enlace (PGO y LTO), consulta `contrib/pgo-lto/Makefile` ([#45641](https://github.com/JuliaLang/julia/issues/45641)).

## New library functions

  * Tres nuevos tipos en torno a la idea de texto con "anotaciones" (`Pair{Symbol, Any}` entradas, por ejemplo, `:lang => "en"` o `:face => :magenta`). Estas anotaciones se conservan a través de las operaciones (por ejemplo, la concatenación de cadenas con `*`) cuando es posible.

      * `AnnotatedString` es un nuevo tipo de `AbstractString`. Envuelve una cadena subyacente y permite que se adjunten anotaciones a regiones de la cadena. Este tipo se utiliza extensamente en la nueva biblioteca estándar `StyledStrings` para contener información de estilo.
      * `AnnotatedChar` es un nuevo tipo de `AbstractChar`. Envuelve otro char y mantiene una lista de anotaciones que se aplican a él.
      * `AnnotatedIOBuffer` es un nuevo tipo de `IO` que imita un `IOBuffer`, pero tiene métodos `read`/`write` especializados para contenido anotado. Esto se puede pensar tanto como un "constructor de cadenas" de cierta manera, como también un pegamento entre contenido anotado y no anotado.
  * `in!(x, s::AbstractSet)` devolverá si `x` está en `s`, e insertará `x` en `s` si no está ([#45156](https://github.com/JuliaLang/julia/issues/45156), [#51636](https://github.com/JuliaLang/julia/issues/51636)).
  * La nueva función `Libc.mkfifo` envuelve la función `mkfifo` de C en plataformas Unix ([#34587](https://github.com/JuliaLang/julia/issues/34587)).
  * `logrange(inicio, parada; longitud)` crea un rango de razón constante, en lugar de paso constante ([#39071](https://github.com/JuliaLang/julia/issues/39071))
  * `copyuntil(out, io, delim)` y `copyline(out, io)` copian datos en un flujo `out::IO` ([#48273](https://github.com/JuliaLang/julia/issues/48273)).
  * `eachrsplit(string, pattern)` itera sobre las subcadenas divididas de derecha a izquierda ([#51646](https://github.com/JuliaLang/julia/issues/51646)).
  * `Sys.username()` se puede usar para devolver el nombre de usuario del usuario actual ([#51897](https://github.com/JuliaLang/julia/issues/51897)).
  * `Sys.isreadable(), Sys.iswritable()` se pueden usar para verificar si el usuario actual tiene permisos de acceso que permiten leer y escribir, respectivamente. ([#53320](https://github.com/JuliaLang/julia/issues/53320)).
  * `GC.logging_enabled()` se puede usar para probar si el registro de GC ha sido habilitado a través de `GC.enable_logging` ([#51647](https://github.com/JuliaLang/julia/issues/51647)).
  * `IdSet` ahora se exporta desde Base y se considera público ([#53262](https://github.com/JuliaLang/julia/issues/53262)).
  * `@time` ahora informa un conteo de cualquier conflicto de bloqueo donde un `ReentrantLock` tuvo que esperar, además de un nuevo macro `@lock_conflicts` que devuelve ese conteo ([#52883](https://github.com/JuliaLang/julia/issues/52883)).
  * El nuevo macro `Base.Cartesian.@ncallkw` es análogo a `Base.Cartesian.@ncall`, pero permite agregar argumentos de palabra clave a la llamada de función ([#51501](https://github.com/JuliaLang/julia/issues/51501)).
  * Nueva función `Docs.hasdoc(module, symbol)` indica si un nombre tiene una cadena de documentación ([#52139](https://github.com/JuliaLang/julia/issues/52139)).
  * Nueva función `Docs.undocumented_names(module)` devuelve los nombres públicos no documentados de un módulo ([#52413](https://github.com/JuliaLang/julia/issues/52413)).

## New library features

  * `invmod(n, T)` donde `T` es un tipo de entero nativo ahora calcula el inverso modular de `n` en el anillo de enteros modulares que define `T` ([#52180](https://github.com/JuliaLang/julia/issues/52180)).
  * `invmod(n)` es una abreviatura de `invmod(n, typeof(n))` para tipos de enteros nativos ([#52180](https://github.com/JuliaLang/julia/issues/52180)).
  * `replace(string, pattern...)` ahora admite un argumento `IO` opcional para escribir la salida en un flujo en lugar de devolver una cadena ([#48625](https://github.com/JuliaLang/julia/issues/48625)).
  * Nuevos métodos `allequal(f, itr)` y `allunique(f, itr)` que toman una función de predicado ([#47679](https://github.com/JuliaLang/julia/issues/47679)).
  * `sizehint!(s, n)` ahora admite un argumento opcional `shrink` para deshabilitar la reducción ([#51929](https://github.com/JuliaLang/julia/issues/51929)).
  * Pasar un `IOBuffer` como argumento stdout para `Process` spawn ahora funciona como se esperaba, sincronizado con `wait` o `success`, por lo que ya no se requiere un `Base.BufferStream` allí para la corrección y evitar condiciones de carrera ([#52461](https://github.com/JuliaLang/julia/issues/52461)).
  * Después de que un proceso sale, `closewrite` ya no se llamará automáticamente en el flujo que se le pasó. Llama a `wait` en el proceso en su lugar para asegurarte de que el contenido esté completamente escrito, luego llama a `closewrite` manualmente para evitar condiciones de carrera, o usa la forma de callback de `open` para que todo eso se maneje automáticamente ([#52461](https://github.com/JuliaLang/julia/issues/52461)).
  * `@timed` ahora devuelve además el tiempo de compilación y recompilación transcurrido ([#52889](https://github.com/JuliaLang/julia/issues/52889)).
  * `filter` ahora puede actuar sobre un `NamedTuple` ([#50795](https://github.com/JuliaLang/julia/issues/50795)).
  * `Iterators.cycle(iter, n)` recorre `iter` un número fijo de veces, en lugar de para siempre ([#47354](https://github.com/JuliaLang/julia/issues/47354)).
  * `zero(::AbstractArray)` ahora se aplica recursivamente, por lo que `zero([[1,2],[3,4,5]])` ahora produce la identidad aditiva `[[0,0],[0,0,0]]` en lugar de generar un error ([#38064](https://github.com/JuliaLang/julia/issues/38064)).
  * `include_dependency(path; track_content=true)` permite cambiar de usar `mtime` a hashing de la dependencia de precompilación para restaurar la relocatibilidad de las cachés de precompilación ([#51798](https://github.com/JuliaLang/julia/issues/51798)).

## Standard library changes

  * El método de respaldo `write(::IO, ::AbstractArray)` que solía llamar recursivamente a `write` en cada elemento, ahora escribe la representación en memoria de cada valor. Por ejemplo, `write(io, 'a':'b')` ahora escribe 4 bytes para cada carácter, en lugar de escribir la representación UTF-8 de cada carácter. El nuevo formato es compatible con el utilizado por `Array`, lo que hace posible usar `read!` para recuperar los datos ([#42593](https://github.com/JuliaLang/julia/issues/42593)).
  * No es posible definir `length` para iteradores con estado de manera generalmente consistente. El potencial de resultados incorrectos de manera silenciosa para los iteradores `Stateful` se aborda eliminando el método `length(::Stateful)`. El último parámetro de tipo de `Stateful` también ha desaparecido. Problema: ([#47790](https://github.com/JuliaLang/julia/issues/47790)), PR: ([#51747](https://github.com/JuliaLang/julia/issues/51747)).

#### Package Manager

  * Ahora es posible especificar "fuentes" para paquetes en una sección `[sources]` en Project.toml. Esto se puede utilizar para agregar dependencias normales o de prueba no registradas.
  * Pkg ahora obedece los límites de `[compat]` para `julia` y genera un error si la versión del binario de Julia en ejecución es incompatible con los límites en `Project.toml`. Pkg siempre ha obedecido esta compatibilidad al trabajar con paquetes de Registro. Este cambio afecta principalmente a los paquetes locales.
  * `pkg> add` y `Pkg.add` ahora agregarán entradas de compatibilidad para nuevas dependencias directas si el entorno activo es un paquete (tiene una entrada `name` y `uuid`).
  * Las dependencias ahora se pueden agregar directamente como dependencias débiles o extras a través de las formas `pkg> add --weak/extra Foo` o `Pkg.add("Foo", target=:weakdeps/:extras)`.

#### StyledStrings

  * Una nueva biblioteca estándar para manejar el estilo de una manera más completa y estructurada ([#49586](https://github.com/JuliaLang/julia/issues/49586)).
  * La nueva estructura `Faces` sirve como un contenedor para la información de estilo de texto (piensa en la tipografía, así como en el color y la decoración), y viene con un marco para proporcionar un enfoque conveniente, extensible (a través de `addface!`) y personalizable (con el `Faces.toml` de un usuario y `loadfaces!`) para contenido estilizado ([#49586](https://github.com/JuliaLang/julia/issues/49586)).
  * El nuevo macro de cadena `@styled_str` proporciona una forma conveniente de crear un `AnnotatedString` con varias caras u otros atributos aplicados ([#49586](https://github.com/JuliaLang/julia/issues/49586)).

#### Libdl

  * Un nuevo tipo `LazyLibrary` se exporta de `Libdl` para su uso en la construcción de cargas de bibliotecas perezosas encadenadas, principalmente para ser utilizado dentro de JLLs ([#50074](https://github.com/JuliaLang/julia/issues/50074)).

#### LinearAlgebra

  * `cbrt(::AbstractMatrix{<:Real})` ahora está definido y devuelve raíces cúbicas de matrices de valores reales de matrices de valores reales. ([#50661](https://github.com/JuliaLang/julia/issues/50661))
  * `eigvals/eigen(A, bunchkaufman(B))` y `eigvals/eigen(A, lu(B))`, que utilizan la descomposición Bunchkaufman (LDL) y LU de `B`, respectivamente, ahora calculan de manera eficiente los valores propios generalizados (`eigen`: y vectores propios) de `A` y `B`. Nota: El segundo argumento es la salida de `bunchkaufman` o `lu` ([#50471](https://github.com/JuliaLang/julia/issues/50471)).
  * Ahora hay un despacho especializado para `eigvals/eigen(::Hermitian{<:Tridiagonal})` que realiza una transformación de similitud para crear una matriz tridiagonal simétrica real y resolverla utilizando las rutinas LAPACK ([#49546](https://github.com/JuliaLang/julia/issues/49546)).
  * Las matrices estructuradas ahora retienen ya sea los ejes del padre (para `Simétrica`/`Hermítica`/`AbstractTriangular`/`UpperHessenberg`), o los de la diagonal principal (para matrices en banda) ([#52480](https://github.com/JuliaLang/julia/issues/52480)).
  * `bunchkaufman` y `bunchkaufman!` ahora funcionan para cualquier `AbstractFloat`, `Rational` y sus variantes complejas. `bunchkaufman` ahora admite tipos `Integer`, al realizar una conversión interna a `Rational{BigInt}`. Se agregó una nueva función `inertia` que calcula la inercia del factor diagonal dado por el objeto de factorización `BunchKaufman` de una matriz simétrica real o hermítica. Para matrices simétricas complejas, `inertia` solo calcula el número de valores propios cero del factor diagonal ([#51487](https://github.com/JuliaLang/julia/issues/51487)).
  * Packages that specialize matrix-matrix `mul!` with a method signature of the form `mul!(::AbstractMatrix, ::MyMatrix, ::AbstractMatrix, ::Number, ::Number)` no longer encounter method ambiguities when interacting with `LinearAlgebra`. Previously, ambiguities used to arise when multiplying a `MyMatrix` with a structured matrix type provided by LinearAlgebra, such as `AbstractTriangular`, which used to necessitate additional methods to resolve such ambiguities. Similar sources of ambiguities have also been removed for matrix-vector `mul!` operations ([#52837](https://github.com/JuliaLang/julia/issues/52837)).
  * `lu` e `issuccess(::LU)` ahora aceptan un argumento clave `allowsingular`. Cuando se establece en `true`, una factorización válida con un factor U de rango deficiente se tratará como un éxito en lugar de lanzar un error. Tales factorizaciones ahora se muestran imprimiendo los factores junto con una nota de "rango deficiente" en lugar de imprimir un mensaje de "Factorización fallida" ([#52957](https://github.com/JuliaLang/julia/issues/52957)).

#### Random

  * `rand` ahora admite muestreo sobre tipos `Tuple` ([#35856](https://github.com/JuliaLang/julia/issues/35856), [#50251](https://github.com/JuliaLang/julia/issues/50251)).
  * `rand` ahora admite muestreo sobre tipos `Pair` ([#28705](https://github.com/JuliaLang/julia/issues/28705)).
  * Al sembrar generadores de números aleatorios (RNG) proporcionados por `Random`, ahora se pueden usar semillas de enteros negativos ([#51416](https://github.com/JuliaLang/julia/issues/51416)).
  * Los generadores de números aleatorios con semilla de `Random` ahora pueden ser sembrados con una cadena, por ejemplo, `seed!(rng, "una semilla aleatoria")` ([#51527](https://github.com/JuliaLang/julia/issues/51527)).

#### REPL

  * Las pistas de autocompletado ahora se muestran en texto más claro mientras se escribe en el repl. Para desactivar, establece `Base.active_repl.options.hint_tab_completes = false` de forma interactiva, o en startup.jl:

    ```
    if VERSION >= v"1.11.0-0"
      atreplinit() do repl
          repl.options.hint_tab_completes = false
      end
    end
    ```

    ([#51229](https://github.com/JuliaLang/julia/issues/51229)).
  * Meta-M con un aviso vacío ahora alterna el módulo contextual entre el módulo contextual anterior no-Main y Main, de modo que cambiar de un lado a otro sea simple ([#51616](https://github.com/JuliaLang/julia/issues/51616), [#52670](https://github.com/JuliaLang/julia/issues/52670)).

#### Dates

La función no documentada `adjust` ya no se exporta, pero ahora está documentada ([#53092](https://github.com/JuliaLang/julia/issues/53092)).

#### Statistics

  * Las estadísticas son ahora una biblioteca estándar actualizable ([#46501](https://github.com/JuliaLang/julia/issues/46501)).

#### Distributed

  * `pmap` ahora utiliza por defecto un `CachingPool` ([#33892](https://github.com/JuliaLang/julia/issues/33892)).

## Deprecated or removed

  * `Base.map`, `Iterators.map` y `foreach` perdieron sus métodos de un solo argumento ([#52631](https://github.com/JuliaLang/julia/issues/52631)).

## External dependencies

  * La biblioteca libuv se ha actualizado de una base de v1.44.2 a v1.48.0 ([#49937](https://github.com/JuliaLang/julia/issues/49937)).
  * `tput` ya no se llama para verificar las capacidades del terminal; ha sido reemplazado por un analizador de terminfo en puro Julia ([#50797](https://github.com/JuliaLang/julia/issues/50797)).
  * La base de datos de información del terminal, `terminfo`, ahora se incluye por defecto, proporcionando una mejor experiencia de usuario en el REPL cuando `terminfo` no está disponible en el sistema. Julia se puede compilar sin incluir la base de datos utilizando la opción del Makefile `WITH_TERMINFO=0`. ([#55411](https://github.com/JuliaLang/julia/issues/55411))

## Tooling Improvements

  * CI now performs limited automatic typo detection on all PRs. If you merge a PR with a failing typo CI check, then the reported typos will be automatically ignored in future CI runs on PRs that edit those same files ([#51704](https://github.com/JuliaLang/julia/issues/51704)).
