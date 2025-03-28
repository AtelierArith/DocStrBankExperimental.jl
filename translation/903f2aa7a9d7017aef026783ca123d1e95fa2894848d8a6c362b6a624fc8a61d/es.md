# [Scoped Values](@id scoped-values)

Los valores con alcance proporcionan una implementación de alcance dinámico en Julia.

!!! note "Lexical scoping vs dynamic scoping"
    [Lexical scoping](@ref scope-of-variables) es el comportamiento predeterminado en Julia. Bajo el alcance léxico, el alcance de una variable se determina por la estructura léxica (textual) de un programa. Bajo el alcance dinámico, una variable está vinculada al valor asignado más reciente durante la ejecución del programa.


El estado de un valor con alcance depende de la ruta de ejecución del programa. Esto significa que para un valor con alcance puedes observar múltiples valores diferentes de manera concurrente.

!!! compat "Julia 1.11"
    Los valores con alcance se introdujeron en Julia 1.11. En Julia 1.8+ hay una implementación compatible disponible en el paquete ScopedValues.jl.


En su forma más simple, puedes crear un [`ScopedValue`](@ref Base.ScopedValues.ScopedValue) con un valor predeterminado y luego usar [`with`](@ref Base.ScopedValues.with) o [`@with`](@ref Base.ScopedValues.@with) para ingresar a un nuevo ámbito dinámico. El nuevo ámbito heredará todos los valores del ámbito padre (y recursivamente de todos los ámbitos exteriores) con el valor de ámbito proporcionado tomando prioridad sobre las definiciones anteriores.

Veamos primero un ejemplo de **ámbito** léxico. Una declaración `let` comienza un nuevo ámbito léxico dentro del cual la definición externa de `x` es oscurecida por su definición interna.

```julia
x = 1
let x = 5
    @show x # 5
end
@show x # 1
```

En el siguiente ejemplo, dado que Julia utiliza el alcance léxico, la variable `x` en el cuerpo de `f` se refiere al `x` definido en el alcance global, y entrar en un alcance `let` no cambia el valor que `f` observa.

```julia
x = 1
f() = @show x
let x = 5
    f() # 1
end
f() # 1
```

Ahora, usando un `ScopedValue`, podemos utilizar el **alcance** dinámico.

```julia
using Base.ScopedValues

x = ScopedValue(1)
f() = @show x[]
with(x=>5) do
    f() # 5
end
f() # 1
```

Tenga en cuenta que el valor observado de `ScopedValue` depende de la ruta de ejecución del programa.

A menudo tiene sentido usar una variable `const` para apuntar a un valor de ámbito, y puedes establecer el valor de múltiples `ScopedValue`s con una sola llamada a `with`.

```julia
using Base.ScopedValues

f() = @show a[]
g() = @show b[]

const a = ScopedValue(1)
const b = ScopedValue(2)

f() # a[] = 1
g() # b[] = 2

# Enter a new dynamic scope and set value.
with(a => 3) do
    f() # a[] = 3
    g() # b[] = 2
    with(a => 4, b => 5) do
        f() # a[] = 4
        g() # b[] = 5
    end
    f() # a[] = 3
    g() # b[] = 2
end

f() # a[] = 1
g() # b[] = 2
```

`ScopedValues` proporciona una versión macro de `with`. La expresión `@with var=>val expr` evalúa `expr` en un nuevo ámbito dinámico con `var` establecido en `val`. `@with var=>val expr` es equivalente a `with(var=>val) do expr end`. Sin embargo, `with` requiere un cierre o función sin argumentos, lo que resulta en un marco de llamada adicional. Como ejemplo, considera la siguiente función `f`:

```julia
using Base.ScopedValues
const a = ScopedValue(1)
f(x) = a[] + x
```

Si deseas ejecutar `f` en un ámbito dinámico con `a` establecido en `2`, entonces puedes usar `with`:

```julia
with(() -> f(10), a=>2)
```

Sin embargo, esto requiere envolver `f` en una función sin argumentos. Si deseas evitar el marco de llamada adicional, entonces puedes usar el macro `@with`:

```julia
@with a=>2 f(10)
```

!!! note
    Los ámbitos dinámicos son heredados por [`Task`](@ref)s, en el momento de la creación de la tarea. Los ámbitos dinámicos **no** se propagan a través de las operaciones de `Distributed.jl`.


En el ejemplo a continuación, abrimos un nuevo ámbito dinámico antes de lanzar una tarea. La tarea principal y las dos tareas secundarias observan valores independientes del mismo valor de ámbito al mismo tiempo.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const scoped_val = ScopedValue(1)
@sync begin
    with(scoped_val => 2)
        @spawn @show scoped_val[] # 2
    end
    with(scoped_val => 3)
        @spawn @show scoped_val[] # 3
    end
    @show scoped_val[] # 1
end
```

Los valores con alcance son constantes a lo largo de un alcance, pero puedes almacenar un estado mutable en un valor con alcance. Solo ten en cuenta que las advertencias habituales para las variables globales se aplican en el contexto de la programación concurrente.

Se requiere cuidado al almacenar referencias a un estado mutable en valores con alcance. Es posible que desee [unshare mutable state](@ref unshare_mutable_state) explícitamente al entrar en un nuevo alcance dinámico.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const sval_dict = ScopedValue(Dict())

# Example of using a mutable value wrongly
@sync begin
    # `Dict` is not thread-safe the usage below is invalid
    @spawn (sval_dict[][:a] = 3)
    @spawn (sval_dict[][:b] = 3)
end

@sync begin
    # If we instead pass a unique dictionary to each
    # task we can access the dictionaries race free.
    with(sval_dict => Dict()) do
        @spawn (sval_dict[][:a] = 3)
    end
    with(sval_dict => Dict()) do
        @spawn (sval_dict[][:b] = 3)
    end
end
```

## Example

En el ejemplo a continuación, utilizamos un valor con alcance para implementar una verificación de permisos en una aplicación web. Después de determinar los permisos de la solicitud, se ingresa a un nuevo alcance dinámico y se establece el valor con alcance `LEVEL`. Otras partes de la aplicación pueden consultar el valor con alcance y recibirán el valor apropiado. Otras alternativas como el almacenamiento local de tareas y las variables globales no son adecuadas para este tipo de propagación; nuestra única alternativa habría sido pasar un valor a través de toda la cadena de llamadas.

```julia
using Base.ScopedValues

const LEVEL = ScopedValue(:GUEST)

function serve(request, response)
    level = isAdmin(request) ? :ADMIN : :GUEST
    with(LEVEL => level) do
        Threads.@spawn handle(request, response)
    end
end

function open(connection::Database)
    level = LEVEL[]
    if level !== :ADMIN
        error("Access disallowed")
    end
    # ... open connection
end

function handle(request, response)
    # ...
    open(Database(#=...=#))
    # ...
end
```

## Idioms

### [Unshare mutable state](@id unshare_mutable_state)

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const sval_dict = ScopedValue(Dict())

# If you want to add new values to the dict, instead of replacing
# it, unshare the values explicitly. In this example we use `merge`
# to unshare the state of the dictionary in parent scope.
@sync begin
    with(sval_dict => merge(sval_dict[], Dict(:a => 10))) do
        @spawn @show sval_dict[][:a]
    end
    @spawn sval_dict[][:a] = 3 # Not a race since they are unshared.
end
```

### Scoped values as globals

Para acceder al valor de un valor con alcance, el valor con alcance en sí mismo debe estar en el (lexical) alcance. Esto significa que, en la mayoría de los casos, es probable que desees usar valores con alcance como constantes globales.

```julia
using Base.ScopedValues
const sval = ScopedValue(1)
```

De hecho, se puede pensar en los valores con alcance como argumentos de función ocultos.

Esto no excluye su uso como no globales.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

function main()
    role = ScopedValue(:client)

    function launch()
        #...
        role[]
    end

    @with role => :server @spawn launch()
    launch()
end
```

Pero podría haber sido más simple simplemente pasar el argumento de la función directamente en estos casos.

### Very many ScopedValues

Si te encuentras creando muchos `ScopedValue` para un módulo dado, puede ser mejor usar una estructura dedicada para contenerlos.

```julia
using Base.ScopedValues

Base.@kwdef struct Configuration
    color::Bool = false
    verbose::Bool = false
end

const CONFIG = ScopedValue(Configuration(color=true))

@with CONFIG => Configuration(color=CONFIG[].color, verbose=true) begin
    @show CONFIG[].color # true
    @show CONFIG[].verbose # true
end
```

## API docs

```@docs
Base.ScopedValues.ScopedValue
Base.ScopedValues.with
Base.ScopedValues.@with
Base.isassigned(::Base.ScopedValues.ScopedValue)
Base.ScopedValues.get
```

## Implementation notes and performance

`Scope`s utilizan un diccionario persistente. La búsqueda y la inserción son `O(log(32, n))`, al entrar en un ámbito dinámico se copia una pequeña cantidad de datos y los datos no modificados se comparten entre otros ámbitos.

El objeto `Scope` en sí mismo no está destinado a los usuarios y puede ser modificado en una futura versión de Julia.

## Design inspiration

Este diseño fue fuertemente inspirado por [JEPS-429](https://openjdk.org/jeps/429), que a su vez fue inspirado por variables libres de ámbito dinámico en muchos dialectos de Lisp. En particular, Interlisp-D y su estrategia de enlace profundo.

Un diseño previo discutido fue variables de contexto como [PEPS-567](https://peps.python.org/pep-0567/) e implementado en Julia como [ContextVariablesX.jl](https://github.com/tkf/ContextVariablesX.jl).
