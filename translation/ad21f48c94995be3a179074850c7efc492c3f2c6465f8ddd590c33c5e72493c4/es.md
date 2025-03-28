```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Logging/docs/src/index.md"
```

# [Logging](@id man-logging)

El módulo [`Logging`](@ref Logging.Logging) proporciona una forma de registrar la historia y el progreso de un cálculo como un registro de eventos. Los eventos se crean insertando una declaración de registro en el código fuente, por ejemplo:

```julia
@warn "Abandon printf debugging, all ye who enter here!"
┌ Warning: Abandon printf debugging, all ye who enter here!
└ @ Main REPL[1]:1
```

El sistema ofrece varias ventajas sobre el uso de `println()` en tu código fuente. Primero, te permite controlar la visibilidad y presentación de los mensajes sin editar el código fuente. Por ejemplo, en contraste con el `@warn` anterior.

```julia
@debug "The sum of some values $(sum(rand(100)))"
```

no producirá ninguna salida por defecto. Además, es muy barato dejar declaraciones de depuración como esta en el código fuente porque el sistema evita evaluar el mensaje si más tarde se ignoraría. En este caso, `sum(rand(100))` y el procesamiento de cadenas asociado nunca se ejecutarán a menos que se habilite el registro de depuración.

En segundo lugar, las herramientas de registro te permiten adjuntar datos arbitrarios a cada evento como un conjunto de pares clave-valor. Esto te permite capturar variables locales y otro estado del programa para un análisis posterior. Por ejemplo, para adjuntar la variable de arreglo local `A` y la suma de un vector `v` como la clave `s`, puedes usar

```jldoctest
A = ones(Int, 4, 4)
v = ones(100)
@info "Some variables"  A  s=sum(v)

# output
┌ Info: Some variables
│   A =
│    4×4 Matrix{Int64}:
│     1  1  1  1
│     1  1  1  1
│     1  1  1  1
│     1  1  1  1
└   s = 100.0
```

Todos los macros de registro `@debug`, `@info`, `@warn` y `@error` comparten características comunes que se describen en detalle en la documentación del macro más general [`@logmsg`](@ref).

## Log event structure

Cada evento genera varias piezas de datos, algunas proporcionadas por el usuario y otras extraídas automáticamente. Examinemos primero los datos definidos por el usuario:

  * El *nivel de registro* es una categoría amplia para el mensaje que se utiliza para el filtrado temprano. Hay varios niveles estándar de tipo [`LogLevel`](@ref); también son posibles niveles definidos por el usuario. Cada uno es distinto en propósito:

      * [`Logging.Debug`](@ref) (nivel de registro -1000) es información destinada al desarrollador del programa. Estos eventos están deshabilitados por defecto.
      * [`Logging.Info`](@ref) (nivel de registro 0) es para información general al usuario. Piénsalo como una alternativa a usar `println` directamente.
      * [`Logging.Warn`](@ref) (nivel de registro 1000) significa que algo está mal y es probable que se requiera acción, pero que por ahora el programa sigue funcionando.
      * [`Logging.Error`](@ref) (nivel de registro 2000) significa que algo está mal y es poco probable que se recupere, al menos por esta parte del código. A menudo, este nivel de registro no es necesario, ya que lanzar una excepción puede transmitir toda la información requerida.
  * El *mensaje* es un objeto que describe el evento. Por convención, los `AbstractString`s pasados como mensajes se asumen en formato markdown. Otros tipos se mostrarán utilizando `print(io, obj)` o `string(obj)` para salida basada en texto y posiblemente `show(io,mime,obj)` para otras visualizaciones multimedia utilizadas en el registrador instalado.
  * Los *pares clave-valor* opcionales permiten adjuntar datos arbitrarios a cada evento. Algunas claves tienen un significado convencional que puede afectar la forma en que se interpreta un evento (ver [`@logmsg`](@ref)).

El sistema también genera información estándar para cada evento:

  * El `módulo` en el que se expandió el macro de registro.
  * El `archivo` y `línea` donde ocurre el macro de registro en el código fuente.
  * Un mensaje `id` que es un identificador único y fijo para la *declaración de código fuente* donde aparece el macro de registro. Este identificador está diseñado para ser bastante estable incluso si el código fuente del archivo cambia, siempre que la declaración de registro en sí misma permanezca igual.
  * Un `grupo` para el evento, que se establece en el nombre base del archivo por defecto, sin extensión. Esto se puede utilizar para agrupar mensajes en categorías más finas que el nivel de registro (por ejemplo, todas las advertencias de deprecación tienen el grupo `:depwarn`), o en agrupaciones lógicas a través de o dentro de módulos.

Tenga en cuenta que información útil como la hora del evento no se incluye por defecto. Esto se debe a que dicha información puede ser costosa de extraer y también está *disponible dinámicamente* para el registrador actual. Es simple definir un [custom logger](@ref AbstractLogger-interface) para aumentar los datos del evento con la hora, la traza de la pila, los valores de las variables globales y otra información útil según sea necesario.

## Processing log events

Como puedes ver en los ejemplos, las declaraciones de registro no mencionan dónde van los eventos de registro ni cómo se procesan. Esta es una característica clave del diseño que hace que el sistema sea componible y natural para su uso concurrente. Lo hace separando dos preocupaciones diferentes:

  * *Crear* eventos de registro es la preocupación del autor del módulo que necesita decidir dónde se activan los eventos y qué información incluir.
  * *Procesamiento* de eventos de registro — es decir, visualización, filtrado, agregación y grabación — es la preocupación del autor de la aplicación que necesita reunir múltiples módulos en una aplicación cooperativa.

### Loggers

El procesamiento de eventos es realizado por un *logger*, que es la primera pieza de código configurable por el usuario que ve el evento. Todos los loggers deben ser subtipos de [`AbstractLogger`](@ref).

Cuando se activa un evento, se encuentra el registrador apropiado buscando un registrador local de tarea con el registrador global como respaldo. La idea aquí es que el código de la aplicación sabe cómo se deben procesar los eventos de registro y existe en algún lugar en la parte superior de la pila de llamadas. Por lo tanto, debemos buscar hacia arriba a través de la pila de llamadas para descubrir el registrador; es decir, el registrador debe tener un *alcance dinámico*. (Este es un punto de contraste con los marcos de registro donde el registrador tiene un *alcance léxico*; proporcionado explícitamente por el autor del módulo o como una simple variable global. En tal sistema, es incómodo controlar el registro mientras se compone funcionalidad de múltiples módulos.)

El registrador global se puede configurar con [`global_logger`](@ref), y los registradores locales de tareas se controlan utilizando [`with_logger`](@ref). Las tareas recién creadas heredan el registrador de la tarea padre.

Hay tres tipos de registradores proporcionados por la biblioteca.  [`ConsoleLogger`](@ref) es el registrador predeterminado que ves al iniciar el REPL.  Muestra eventos en un formato de texto legible y trata de ofrecer un control simple pero amigable sobre el formato y el filtrado.  [`NullLogger`](@ref) es una forma conveniente de descartar todos los mensajes cuando sea necesario; es el equivalente de registro del flujo [`devnull`](@ref).  [`SimpleLogger`](@ref) es un registrador de formato de texto muy simplista, principalmente útil para depurar el sistema de registro en sí.

Los registradores personalizados deben venir con sobrecargas para las funciones descritas en el [reference section](@ref AbstractLogger-interface).

### Early filtering and message handling

Cuando ocurre un evento, se realizan algunos pasos de filtrado temprano para evitar generar mensajes que serán descartados:

1. El nivel de registro de mensajes se verifica contra un nivel mínimo global (establecido a través de [`disable_logging`](@ref)). Este es un ajuste global rudimentario pero extremadamente económico.
2. El estado actual del registrador se consulta y el nivel del mensaje se verifica en comparación con el nivel mínimo en caché del registrador, como se encuentra al llamar a [`Logging.min_enabled_level`](@ref). Este comportamiento se puede anular a través de variables de entorno (más sobre esto más adelante).
3. La función [`Logging.shouldlog`](@ref) se llama con el registrador actual, tomando alguna información mínima (nivel, módulo, grupo, id) que puede ser calculada estáticamente. Más útilmente, `shouldlog` recibe un evento `id` que puede ser utilizado para descartar eventos temprano basado en un predicado en caché.

Si todas estas verificaciones pasan, el mensaje y los pares clave-valor se evalúan en su totalidad y se pasan al registrador actual a través de la función [`Logging.handle_message`](@ref). `handle_message()` puede realizar filtrados adicionales según sea necesario y mostrar el evento en la pantalla, guardarlo en un archivo, etc.

Las excepciones que ocurren al generar el evento de registro se capturan y registran por defecto. Esto evita que eventos individuales rotos hagan que la aplicación se bloquee, lo cual es útil al habilitar eventos de depuración poco utilizados en un sistema de producción. Este comportamiento se puede personalizar por tipo de registrador extendiendo [`Logging.catch_exceptions`](@ref).

## Testing log events

Los eventos de registro son un efecto secundario de ejecutar código normal, pero es posible que desees probar mensajes informativos y advertencias particulares. El módulo `Test` proporciona un macro [`@test_logs`](@ref) que se puede utilizar para hacer coincidencias de patrones contra el flujo de eventos de registro.

## Environment variables

El filtrado de mensajes puede ser influenciado a través de la variable de entorno [`JULIA_DEBUG`](@ref JULIA_DEBUG), y sirve como una forma sencilla de habilitar el registro de depuración para un archivo o módulo. Cargar julia con `JULIA_DEBUG=loading` activará los mensajes de registro `@debug` en `loading.jl`. Por ejemplo, en las terminales de Linux:

```
$ JULIA_DEBUG=loading julia -e 'using OhMyREPL'
┌ Debug: Rejecting cache file /home/user/.julia/compiled/v0.7/OhMyREPL.ji due to it containing an incompatible cache header
└ @ Base loading.jl:1328
[ Info: Recompiling stale cache file /home/user/.julia/compiled/v0.7/OhMyREPL.ji for module OhMyREPL
┌ Debug: Rejecting cache file /home/user/.julia/compiled/v0.7/Tokenize.ji due to it containing an incompatible cache header
└ @ Base loading.jl:1328
...
```

En Windows, lo mismo se puede lograr en `CMD` ejecutando primero `set JULIA_DEBUG="loading"` y en `Powershell` a través de `$env:JULIA_DEBUG="loading"`.

De manera similar, la variable de entorno se puede utilizar para habilitar el registro de depuración de módulos, como `Pkg`, o raíces de módulos (ver [`Base.moduleroot`](@ref)). Para habilitar todos los registros de depuración, utiliza el valor especial `all`.

Para activar el registro de depuración desde el REPL, establece `ENV["JULIA_DEBUG"]` al nombre del módulo de interés. Las funciones definidas en el REPL pertenecen al módulo `Main`; el registro para ellas se puede habilitar de esta manera:

```julia-repl
julia> foo() = @debug "foo"
foo (generic function with 1 method)

julia> foo()

julia> ENV["JULIA_DEBUG"] = Main
Main

julia> foo()
┌ Debug: foo
└ @ Main REPL[1]:1

```

Utiliza un separador de comas para habilitar la depuración de múltiples módulos: `JULIA_DEBUG=loading,Main`.

## Examples

### Example: Writing log events to a file

A veces puede ser útil escribir eventos de registro en un archivo. Aquí hay un ejemplo de cómo usar un registrador local de tarea y un registrador global para escribir información en un archivo de texto:

```julia-repl
# Load the logging module
julia> using Logging

# Open a textfile for writing
julia> io = open("log.txt", "w+")
IOStream(<file log.txt>)

# Create a simple logger
julia> logger = SimpleLogger(io)
SimpleLogger(IOStream(<file log.txt>), Info, Dict{Any,Int64}())

# Log a task-specific message
julia> with_logger(logger) do
           @info("a context specific log message")
       end

# Write all buffered messages to the file
julia> flush(io)

# Set the global logger to logger
julia> global_logger(logger)
SimpleLogger(IOStream(<file log.txt>), Info, Dict{Any,Int64}())

# This message will now also be written to the file
julia> @info("a global log message")

# Close the file
julia> close(io)
```

### Example: Enable debug-level messages

Aquí hay un ejemplo de crear un [`ConsoleLogger`](@ref) que permite pasar cualquier mensaje con un nivel de registro mayor o igual a [`Logging.Debug`](@ref).

```julia-repl
julia> using Logging

# Create a ConsoleLogger that prints any log messages with level >= Debug to stderr
julia> debuglogger = ConsoleLogger(stderr, Logging.Debug)

# Enable debuglogger for a task
julia> with_logger(debuglogger) do
           @debug "a context specific log message"
       end

# Set the global logger
julia> global_logger(debuglogger)
```

## Reference

### Logging module

```@docs
Logging.Logging
```

### Creating events

```@docs
Logging.@logmsg
Logging.LogLevel
Logging.Debug
Logging.Info
Logging.Warn
Logging.Error
Logging.BelowMinLevel
Logging.AboveMaxLevel
```

### [Processing events with AbstractLogger](@id AbstractLogger-interface)

El procesamiento de eventos se controla mediante la sobrescritura de funciones asociadas con `AbstractLogger`:

| Methods to implement                |                        | Brief description                            |
|:----------------------------------- |:---------------------- |:-------------------------------------------- |
| [`Logging.handle_message`](@ref)    |                        | Handle a log event                           |
| [`Logging.shouldlog`](@ref)         |                        | Early filtering of events                    |
| [`Logging.min_enabled_level`](@ref) |                        | Lower bound for log level of accepted events |
| **Optional methods**                | **Default definition** | **Brief description**                        |
| [`Logging.catch_exceptions`](@ref)  | `true`                 | Catch exceptions during event evaluation     |

```@docs
Logging.AbstractLogger
Logging.handle_message
Logging.shouldlog
Logging.min_enabled_level
Logging.catch_exceptions
Logging.disable_logging
```

### Using Loggers

Instalación e inspección del registrador:

```@docs
Logging.global_logger
Logging.with_logger
Logging.current_logger
```

Registros que se suministran con el sistema:

```@docs
Logging.NullLogger
Logging.ConsoleLogger
Logging.SimpleLogger
```
