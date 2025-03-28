# [Modules](@id modules)

Los módulos en Julia ayudan a organizar el código en unidades coherentes. Están delimitados sintácticamente dentro de `module NombreDelModulo ... end`, y tienen las siguientes características:

1. Los módulos son espacios de nombres separados, cada uno introduciendo un nuevo ámbito global. Esto es útil, porque permite que el mismo nombre se use para diferentes funciones o variables globales sin conflicto, siempre que estén en módulos separados.
2. Los módulos tienen facilidades para la gestión detallada de espacios de nombres: cada uno define un conjunto de nombres que `exporta` y marca como `público`, y puede importar nombres de otros módulos con `using` e `import` (explicamos esto a continuación).
3. Los módulos se pueden precompilar para una carga más rápida y pueden contener código para la inicialización en tiempo de ejecución.

Típicamente, en paquetes más grandes de Julia verás el código del módulo organizado en archivos, por ejemplo

```julia
module SomeModule

# export, public, using, import statements are usually here; we discuss these below

include("file1.jl")
include("file2.jl")

end
```

Los archivos y los nombres de archivo son en su mayoría irrelevantes para los módulos; los módulos están asociados solo con expresiones de módulo. Se pueden tener múltiples archivos por módulo y múltiples módulos por archivo. `include` se comporta como si el contenido del archivo fuente se evaluara en el ámbito global del módulo que lo incluye. En este capítulo, utilizamos ejemplos cortos y simplificados, por lo que no usaremos `include`.

El estilo recomendado es no sangrar el cuerpo del módulo, ya que eso típicamente llevaría a que archivos enteros estén sangrados. Además, es común usar `UpperCamelCase` para los nombres de los módulos (al igual que para los tipos), y usar la forma plural si es aplicable, especialmente si el módulo contiene un identificador con un nombre similar, para evitar conflictos de nombres. Por ejemplo,

```julia
module FastThings

struct FastThing
    ...
end

end
```

## [Namespace management](@id namespace-management)

La gestión de espacios de nombres se refiere a las facilidades que el lenguaje ofrece para hacer que los nombres en un módulo estén disponibles en otros módulos. Discutimos los conceptos y la funcionalidad relacionados a continuación en detalle.

### Qualified names

Los nombres de funciones, variables y tipos en el ámbito global como `sin`, `ARGS` y `UnitRange` siempre pertenecen a un módulo, llamado el *módulo padre*, que se puede encontrar interactivamente con [`parentmodule`](@ref), por ejemplo.

```jldoctest
julia> parentmodule(UnitRange)
Base
```

Uno también puede referirse a estos nombres fuera de su módulo padre prefijándolos con su módulo, por ejemplo `Base.UnitRange`. Esto se llama un *nombre calificado*. El módulo padre puede ser accesible utilizando una cadena de submódulos como `Base.Math.sin`, donde `Base.Math` se llama la *ruta del módulo*. Debido a ambigüedades sintácticas, calificar un nombre que contiene solo símbolos, como un operador, requiere insertar dos puntos, por ejemplo `Base.:+`. Un pequeño número de operadores además requiere paréntesis, por ejemplo `Base.:(==)`.

Si un nombre está calificado, entonces siempre es *accesible*, y en el caso de una función, también se le pueden agregar métodos utilizando el nombre calificado como el nombre de la función.

Dentro de un módulo, un nombre de variable puede ser "reservado" sin asignarle un valor al declararlo como `global x`. Esto previene conflictos de nombres para las variables globales inicializadas después del tiempo de carga. La sintaxis `M.x = y` no funciona para asignar una variable global en otro módulo; la asignación global siempre es local al módulo.

### Export lists

Los nombres (que se refieren a funciones, tipos, variables globales y constantes) se pueden agregar a la *lista de exportación* de un módulo con `export`: estos son los símbolos que se importan al usar el módulo. Típicamente, están al principio o cerca de la parte superior de la definición del módulo para que los lectores del código fuente puedan encontrarlos fácilmente, como en

```jldoctest module_manual
julia> module NiceStuff
       export nice, DOG
       struct Dog end      # singleton type, not exported
       const DOG = Dog()   # named instance, exported
       nice(x) = "nice $x" # function, exported
       end;

```

pero esto es solo una sugerencia de estilo: un módulo puede tener múltiples declaraciones `export` en ubicaciones arbitrarias.

Es común exportar nombres que forman parte de la API (interfaz de programación de aplicaciones). En el código anterior, la lista de exportación sugiere que los usuarios deben usar `nice` y `DOG`. Sin embargo, dado que los nombres calificados siempre hacen que los identificadores sean accesibles, esta es solo una opción para organizar las API: a diferencia de otros lenguajes, Julia no tiene facilidades para ocultar verdaderamente los internos del módulo.

Además, algunos módulos no exportan nombres en absoluto. Esto se hace generalmente si utilizan palabras comunes, como `derivada`, en su API, lo que podría chocar fácilmente con las listas de exportación de otros módulos. Veremos cómo gestionar los conflictos de nombres a continuación.

To mark a name as public without exporting it into the namespace of folks who call `using NiceStuff`, one can use `public` instead of `export`. This marks the public name(s) as part of the public API, but does not have any namespace implications. The `public` keyword is only available in Julia 1.11 and above. To maintain compatibility with Julia 1.10 and below, use the `@compat` macro from the [Compat](https://github.com/JuliaLang/Compat.jl) package.

### Standalone `using` and `import`

Para uso interactivo, la forma más común de cargar un módulo es `using ModuleName`. Esto [loads](@ref code-loading) el código asociado con `ModuleName`, y trae

1. el nombre del módulo
2. y los elementos de la lista de exportación en el espacio de nombres global circundante.

Técnicamente, la declaración `using ModuleName` significa que un módulo llamado `ModuleName` estará disponible para resolver nombres según sea necesario. Cuando se encuentra una variable global que no tiene definición en el módulo actual, el sistema la buscará entre las variables exportadas por `ModuleName` y la usará si se encuentra allí. Esto significa que todos los usos de esa global dentro del módulo actual se resolverán a la definición de esa variable en `ModuleName`.

Para cargar un módulo de un paquete, se puede usar la instrucción `using ModuleName`. Para cargar un módulo de un módulo definido localmente, se necesita agregar un punto antes del nombre del módulo, como `using .ModuleName`.

Para continuar con nuestro ejemplo,

```jldoctest module_manual
julia> using .NiceStuff
```

cargar el código anterior, haciendo que `NiceStuff` (el nombre del módulo), `DOG` y `nice` estén disponibles. `Dog` no está en la lista de exportación, pero se puede acceder a él si el nombre se califica con la ruta del módulo (que aquí es solo el nombre del módulo) como `NiceStuff.Dog`.

Importante, **`using ModuleName` es la única forma para la cual las listas de exportación importan en absoluto**.

En contraste,

```jldoctest module_manual
julia> import .NiceStuff
```

trae *solo* el nombre del módulo al ámbito. Los usuarios necesitarían usar `NiceStuff.DOG`, `NiceStuff.Dog` y `NiceStuff.nice` para acceder a su contenido. Por lo general, `import ModuleName` se utiliza en contextos cuando el usuario quiere mantener limpio el espacio de nombres. Como veremos en la siguiente sección, `import .NiceStuff` es equivalente a `using .NiceStuff: NiceStuff`.

Puedes combinar múltiples declaraciones `using` e `import` del mismo tipo en una expresión separada por comas, por ejemplo:

```jldoctest module_manual
julia> using LinearAlgebra, Random
```

### `using` and `import` with specific identifiers, and adding methods

Cuando `using ModuleName:` o `import ModuleName:` es seguido por una lista de nombres separados por comas, el módulo se carga, pero *solo esos nombres específicos se traen al espacio de nombres* por la declaración. Por ejemplo,

```jldoctest module_manual
julia> using .NiceStuff: nice, DOG
```

importaré los nombres `nice` y `DOG`.

Importante, el nombre del módulo `NiceStuff` *no* estará en el espacio de nombres. Si deseas hacerlo accesible, debes enumerarlo explícitamente, como

```jldoctest module_manual
julia> using .NiceStuff: nice, DOG, NiceStuff
```

Cuando dos o más paquetes/módulos exportan un nombre y ese nombre no se refiere a lo mismo en cada uno de los paquetes, y los paquetes se cargan a través de `using` sin una lista explícita de nombres, es un error hacer referencia a ese nombre sin calificación. Por lo tanto, se recomienda que el código destinado a ser compatible con versiones futuras de sus dependencias y de Julia, por ejemplo, el código en paquetes liberados, liste los nombres que utiliza de cada paquete cargado, por ejemplo, `using Foo: Foo, f` en lugar de `using Foo`.

Julia tiene dos formas para aparentemente lo mismo porque solo `import ModuleName: f` permite agregar métodos a `f` *sin una ruta de módulo*. Es decir, el siguiente ejemplo dará un error:

```jldoctest module_manual
julia> using .NiceStuff: nice

julia> struct Cat end

julia> nice(::Cat) = "nice 😸"
ERROR: invalid method definition in Main: function NiceStuff.nice must be explicitly imported to be extended
Stacktrace:
 [1] top-level scope
   @ none:0
 [2] top-level scope
   @ none:1

```

Este error evita agregar accidentalmente métodos a funciones en otros módulos que solo pretendías usar.

Hay dos formas de lidiar con esto. Siempre puedes calificar los nombres de las funciones con una ruta de módulo:

```jldoctest module_manual
julia> using .NiceStuff

julia> struct Cat end

julia> NiceStuff.nice(::Cat) = "nice 😸"

```

Alternativamente, puedes `importar` el nombre de la función específica:

```jldoctest module_manual
julia> import .NiceStuff: nice

julia> struct Cat end

julia> nice(::Cat) = "nice 😸"
nice (generic function with 2 methods)
```

Cuál elijas es una cuestión de estilo. La primera forma deja claro que estás añadiendo un método a una función en otro módulo (recuerda que las importaciones y la definición del método pueden estar en archivos separados), mientras que la segunda es más corta, lo que es especialmente conveniente si estás definiendo múltiples métodos.

Una vez que una variable se hace visible a través de `using` o `import`, un módulo no puede crear su propia variable con el mismo nombre. Las variables importadas son de solo lectura; asignar a una variable global siempre afecta a una variable perteneciente al módulo actual, o de lo contrario genera un error.

### Renaming with `as`

Un identificador traído al ámbito por `import` o `using` puede ser renombrado con la palabra clave `as`. Esto es útil para resolver conflictos de nombres así como para acortar nombres. Por ejemplo, `Base` exporta la función llamada `read`, pero el paquete CSV.jl también proporciona `CSV.read`. Si vamos a invocar la lectura de CSV muchas veces, sería conveniente omitir el calificador `CSV.`. Pero entonces es ambiguo si nos referimos a `Base.read` o `CSV.read`:

```julia-repl
julia> read;

julia> import CSV: read
WARNING: ignoring conflicting import of CSV.read into Main
```

Renombrar proporciona una solución:

```julia-repl
julia> import CSV: read as rd
```

Los paquetes importados también se pueden renombrar:

```julia
import BenchmarkTools as BT
```

`as` funciona con `using` solo cuando se trae un único identificador al ámbito. Por ejemplo, `using CSV: read as rd` funciona, pero `using CSV as C` no, ya que opera sobre todos los nombres exportados en `CSV`.

### Mixing multiple `using` and `import` statements

Cuando se utilizan múltiples declaraciones `using` o `import` de cualquiera de las formas anteriores, su efecto se combina en el orden en que aparecen. Por ejemplo,

```jldoctest module_manual
julia> using .NiceStuff         # exported names and the module name

julia> import .NiceStuff: nice  # allows adding methods to unqualified functions

```

traerá todos los nombres exportados de `NiceStuff` y el nombre del módulo en sí al alcance, y también permitirá agregar métodos a `nice` sin prefijarlo con un nombre de módulo.

### Handling name conflicts

Considere la situación en la que dos (o más) paquetes exportan el mismo nombre, como en

```jldoctest module_manual
julia> module A
       export f
       f() = 1
       end
A
julia> module B
       export f
       f() = 2
       end
B
```

La declaración `using .A, .B` funciona, pero cuando intentas llamar a `f`, obtienes un error con una pista.

```jldoctest module_manual
julia> using .A, .B

julia> f
ERROR: UndefVarError: `f` not defined in `Main`
Hint: It looks like two or more modules export different bindings with this name, resulting in ambiguity. Try explicitly importing it from a particular module, or qualifying the name with the module it should come from.
```

Aquí, Julia no puede decidir a qué `f` te refieres, así que tienes que hacer una elección. Las siguientes soluciones son comúnmente utilizadas:

1. Simplemente procede con nombres calificados como `A.f` y `B.f`. Esto hace que el contexto sea claro para el lector de tu código, especialmente si `f` coincide por casualidad pero tiene un significado diferente en varios paquetes. Por ejemplo, `grado` tiene varios usos en matemáticas, ciencias naturales y en la vida cotidiana, y estos significados deben mantenerse separados.
2. Utiliza la palabra clave `as` arriba para renombrar uno o ambos identificadores, por ejemplo

    ```jldoctest module_manual
    julia> using .A: f as f

    julia> using .B: f as g

    ```

    haría que `B.f` estuviera disponible como `g`. Aquí, estamos asumiendo que no usaste `using A` antes, lo que habría traído `f` al espacio de nombres.
3. Cuando los nombres en cuestión *comparten* un significado, es común que un módulo lo importe de otro, o que tenga un paquete "base" ligero con la única función de definir una interfaz como esta, que puede ser utilizada por otros paquetes. Es convencional que tales nombres de paquetes terminen en `...Base` (lo cual no tiene nada que ver con el módulo `Base` de Julia).

### Default top-level definitions and bare modules

Los módulos contienen automáticamente `using Core`, `using Base`, y definiciones de las funciones [`eval`](@ref) y [`include`](@ref), que evalúan expresiones/archivos dentro del ámbito global de ese módulo.

Si no se desean estas definiciones predeterminadas, los módulos se pueden definir utilizando la palabra clave [`baremodule`](@ref) en su lugar (nota: `Core` todavía se importa). En términos de `baremodule`, un `module` estándar se ve así:

```
baremodule Mod

using Base

eval(x) = Core.eval(Mod, x)
include(p) = Base.include(Mod, p)

...

end
```

Si incluso `Core` no es deseado, se puede definir un módulo que no importe nada y no defina nombres en absoluto con `Module(:YourNameHere, false, false)` y el código se puede evaluar en él con [`@eval`](@ref) o [`Core.eval`](@ref):

```jldoctest
julia> arithmetic = Module(:arithmetic, false, false)
Main.arithmetic

julia> @eval arithmetic add(x, y) = $(+)(x, y)
add (generic function with 1 method)

julia> arithmetic.add(12, 13)
25
```

### Standard modules

Hay tres módulos estándar importantes:

  * [`Core`](@ref) contiene toda la funcionalidad "integrada" en el lenguaje.
  * [`Base`](@ref) contiene funcionalidad básica que es útil en casi todos los casos.
  * [`Main`](@ref) es el módulo de nivel superior y el módulo actual, cuando se inicia Julia.

!!! note "Standard library modules"
    Por defecto, Julia viene con algunos módulos de la biblioteca estándar. Estos se comportan como paquetes regulares de Julia, excepto que no necesitas instalarlos explícitamente. Por ejemplo, si quisieras realizar algunas pruebas unitarias, podrías cargar la biblioteca estándar `Test` de la siguiente manera:

    ```julia
    using Test
    ```


## Submodules and relative paths

Los módulos pueden contener *submódulos*, anidando la misma sintaxis `module ... end`. Pueden ser utilizados para introducir espacios de nombres separados, lo que puede ser útil para organizar bases de código complejas. Tenga en cuenta que cada `module` introduce su propio [scope](@ref scope-of-variables), por lo que los submódulos no “heredan” automáticamente nombres de su padre.

Se recomienda que los submódulos se refieran a otros módulos dentro del módulo padre que los contiene (incluyendo este último) utilizando *calificadores de módulo relativos* en las declaraciones `using` e `import`. Un calificador de módulo relativo comienza con un punto (`.`), que corresponde al módulo actual, y cada `.` sucesivo lleva al padre del módulo actual. Esto debe ser seguido por módulos si es necesario, y eventualmente el nombre real a acceder, todos separados por `.`s.

Considere el siguiente ejemplo, donde el submódulo `SubA` define una función, que luego se extiende en su módulo "hermano":

```jldoctest module_manual
julia> module ParentModule
       module SubA
       export add_D  # exported interface
       const D = 3
       add_D(x) = x + D
       end
       using .SubA  # brings `add_D` into the namespace
       export add_D # export it from ParentModule too
       module SubB
       import ..SubA: add_D # relative path for a “sibling” module
       struct Infinity end
       add_D(x::Infinity) = x
       end
       end;

```

Puede ver código en paquetes, que, en una situación similar, utiliza

```jldoctest module_manual
julia> import .ParentModule.SubA: add_D

```

Sin embargo, esto opera a través de [code loading](@ref code-loading), y por lo tanto solo funciona si `ParentModule` está en un paquete. Es mejor usar rutas relativas.

Tenga en cuenta que el orden de las definiciones también importa si está evaluando valores. Considere

```julia
module TestPackage

export x, y

x = 0

module Sub
using ..TestPackage
z = y # ERROR: UndefVarError: `y` not defined in `Main`
end

y = 1

end
```

donde `Sub` está tratando de usar `TestPackage.y` antes de que se defina, por lo que no tiene un valor.

Por razones similares, no puedes usar un orden cíclico:

```julia
module A

module B
using ..C # ERROR: UndefVarError: `C` not defined in `Main.A`
end

module C
using ..B
end

end
```

## Module initialization and precompilation

Los módulos grandes pueden tardar varios segundos en cargarse porque ejecutar todas las declaraciones en un módulo a menudo implica compilar una gran cantidad de código. Julia crea cachés precompilados del módulo para reducir este tiempo.

Los archivos de módulos precompilados (a veces llamados "archivos de caché") se crean y utilizan automáticamente cuando `import` o `using` carga un módulo. Si el(los) archivo(s) de caché aún no existen, el módulo se compilará y se guardará para su reutilización futura. También puedes llamar manualmente a [`Base.compilecache(Base.identify_package("modulename"))`](@ref) para crear estos archivos sin cargar el módulo. Los archivos de caché resultantes se almacenarán en la subcarpeta `compiled` de `DEPOT_PATH[1]`. Si nada sobre tu sistema cambia, tales archivos de caché se utilizarán cuando cargues el módulo con `import` o `using`.

Los archivos de caché de precompilación almacenan definiciones de módulos, tipos, métodos y constantes. También pueden almacenar especializaciones de métodos y el código generado para ellos, pero esto generalmente requiere que el desarrollador agregue directivas explícitas [`precompile`](@ref) o ejecute cargas de trabajo que obliguen a la compilación durante la construcción del paquete.

Sin embargo, si actualizas las dependencias del módulo o cambias su código fuente, el módulo se recompila automáticamente al `usar` o `importar`. Las dependencias son módulos que importa, la construcción de Julia, archivos que incluye, o dependencias explícitas declaradas por [`include_dependency(path)`](@ref) en el/los archivo(s) del módulo.

Para las dependencias de archivos cargadas por `include`, un cambio se determina examinando si el tamaño del archivo (`fsize`) o el contenido (condensado en un hash) no ha cambiado. Para las dependencias de archivos cargadas por `include_dependency`, un cambio se determina examinando si el tiempo de modificación (`mtime`) no ha cambiado, o es igual al tiempo de modificación truncado al segundo más cercano (para acomodar sistemas que no pueden copiar mtime con precisión de sub-segundos). También se tiene en cuenta si la ruta al archivo elegida por la lógica de búsqueda en `require` coincide con la ruta que había creado el archivo de precompilación. También se tiene en cuenta el conjunto de dependencias ya cargadas en el proceso actual y no se recompilarán esos módulos, incluso si sus archivos cambian o desaparecen, para evitar crear incompatibilidades entre el sistema en ejecución y la caché de precompilación. Finalmente, se tiene en cuenta los cambios en cualquier [compile-time preferences](@ref preferences).

Si sabes que un módulo *no* es seguro para precompilar (por ejemplo, por una de las razones descritas a continuación), debes poner `__precompile__(false)` en el archivo del módulo (típicamente colocado en la parte superior). Esto hará que `Base.compilecache` lance un error y hará que `using` / `import` lo cargue directamente en el proceso actual y omita la precompilación y el almacenamiento en caché. Esto también evita que el módulo sea importado por cualquier otro módulo precompilado.

Es posible que necesite estar al tanto de ciertos comportamientos inherentes a la creación de bibliotecas compartidas incrementales que pueden requerir cuidado al escribir su módulo. Por ejemplo, el estado externo no se conserva. Para acomodar esto, separe explícitamente cualquier paso de inicialización que deba ocurrir en *tiempo de ejecución* de los pasos que pueden ocurrir en *tiempo de compilación*. Para este propósito, Julia le permite definir una función `__init__()` en su módulo que ejecuta cualquier paso de inicialización que deba ocurrir en tiempo de ejecución. Esta función no se llamará durante la compilación (`--output-*`). Efectivamente, puede asumir que se ejecutará exactamente una vez en la vida útil del código. Por supuesto, puede llamarla manualmente si es necesario, pero la suposición predeterminada es que esta función se ocupa de calcular el estado para la máquina local, que no necesita ser – o incluso no debería ser – capturado en la imagen compilada. Se llamará después de que el módulo se cargue en un proceso, incluso si se está cargando en una compilación incremental (`--output-incremental=yes`), pero no si se está cargando en un proceso de compilación completa.

En particular, si defines una `function __init__()` en un módulo, entonces Julia llamará a `__init__()` inmediatamente *después* de que el módulo sea cargado (por ejemplo, mediante `import`, `using` o `require`) en tiempo de ejecución por *primera* vez (es decir, `__init__` solo se llama una vez, y solo después de que todas las declaraciones en el módulo han sido ejecutadas). Debido a que se llama después de que el módulo está completamente importado, cualquier submódulo u otros módulos importados tienen sus funciones `__init__` llamadas *antes* que el `__init__` del módulo que lo contiene.

Dos usos típicos de `__init__` son llamar a funciones de inicialización en tiempo de ejecución de bibliotecas externas en C e inicializar constantes globales que involucran punteros devueltos por bibliotecas externas. Por ejemplo, supongamos que estamos llamando a una biblioteca C `libfoo` que requiere que llamemos a una función de inicialización `foo_init()` en tiempo de ejecución. Supongamos que también queremos definir una constante global `foo_data_ptr` que contenga el valor de retorno de una función `void *foo_data()` definida por `libfoo` – esta constante debe ser inicializada en tiempo de ejecución (no en tiempo de compilación) porque la dirección del puntero cambiará de una ejecución a otra. Podrías lograr esto definiendo la siguiente función `__init__` en tu módulo:

```julia
const foo_data_ptr = Ref{Ptr{Cvoid}}(0)
function __init__()
    ccall((:foo_init, :libfoo), Cvoid, ())
    foo_data_ptr[] = ccall((:foo_data, :libfoo), Ptr{Cvoid}, ())
    nothing
end
```

Tenga en cuenta que es perfectamente posible definir una variable global dentro de una función como `__init__`; esta es una de las ventajas de usar un lenguaje dinámico. Pero al convertirla en una constante en el ámbito global, podemos asegurarnos de que el tipo sea conocido por el compilador y permitirle generar un código mejor optimizado. Obviamente, cualquier otra variable global en su módulo que dependa de `foo_data_ptr` también tendría que ser inicializada en `__init__`.

Las constantes que involucran la mayoría de los objetos de Julia que no son producidos por [`ccall`](@ref) no necesitan ser colocadas en `__init__`: sus definiciones pueden ser precompiladas y cargadas desde la imagen del módulo en caché. Esto incluye objetos complicados asignados en el heap, como los arreglos. Sin embargo, cualquier rutina que devuelva un valor de puntero en bruto debe ser llamada en tiempo de ejecución para que la precompilación funcione ([`Ptr`](@ref) los objetos se convertirán en punteros nulos a menos que estén ocultos dentro de un objeto [`isbits`](@ref)). Esto incluye los valores de retorno de las funciones de Julia [`@cfunction`](@ref) y [`pointer`](@ref).

Los tipos de diccionario y conjunto, o en general cualquier cosa que dependa de la salida de un método `hash(key)`, son un caso más complicado. En el caso común donde las claves son números, cadenas, símbolos, rangos, `Expr` o composiciones de estos tipos (a través de arreglos, tuplas, conjuntos, pares, etc.), son seguros para precompilar. Sin embargo, para algunos otros tipos de clave, como `Function` o `DataType` y tipos genéricos definidos por el usuario donde no has definido un método `hash`, el método `hash` por defecto depende de la dirección de memoria del objeto (a través de su `objectid`) y, por lo tanto, puede cambiar de una ejecución a otra. Si tienes uno de estos tipos de clave, o si no estás seguro, para estar seguro puedes inicializar este diccionario desde dentro de tu función `__init__`. Alternativamente, puedes usar el tipo de diccionario [`IdDict`](@ref), que es tratado especialmente por la precompilación para que sea seguro inicializarlo en tiempo de compilación.

Al utilizar la precompilación, es importante mantener una clara distinción entre la fase de compilación y la fase de ejecución. En este modo, a menudo será mucho más evidente que Julia es un compilador que permite la ejecución de código Julia arbitrario, no un intérprete independiente que también genera código compilado.

Otros escenarios de falla potencial conocidos incluyen:

1. Contadores globales (por ejemplo, para intentar identificar objetos de manera única). Considera el siguiente fragmento de código:

    ```julia
    mutable struct UniquedById
        myid::Int
        let counter = 0
            UniquedById() = new(counter += 1)
        end
    end
    ```

    mientras que la intención de este código era dar a cada instancia un id único, el valor del contador se registra al final de la compilación. Todos los usos posteriores de este módulo compilado de forma incremental comenzarán desde ese mismo valor del contador.

    Tenga en cuenta que `objectid` (que funciona mediante el hash del puntero de memoria) tiene problemas similares (consulte las notas sobre el uso de `Dict` a continuación).

    Una alternativa es usar un macro para capturar [`@__MODULE__`](@ref) y almacenarlo solo con el valor actual de `counter`, sin embargo, puede ser mejor rediseñar el código para no depender de este estado global.
2. Las colecciones asociativas (como `Dict` y `Set`) necesitan ser re-hashed en `__init__`. (En el futuro, se puede proporcionar un mecanismo para registrar una función de inicialización.)
3. Dependiendo de los efectos secundarios en tiempo de compilación que persisten a través del tiempo de carga. Ejemplos incluyen: modificar arreglos u otras variables en otros módulos de Julia; mantener manejadores de archivos o dispositivos abiertos; almacenar punteros a otros recursos del sistema (incluida la memoria);
4. Crear "copias" accidentales del estado global de otro módulo, al referenciarlo directamente en lugar de a través de su ruta de búsqueda. Por ejemplo, (en el ámbito global):

    ```julia
    #mystdout = Base.stdout #= will not work correctly, since this will copy Base.stdout into this module =#
    # instead use accessor functions:
    getstdout() = Base.stdout #= best option =#
    # or move the assignment into the runtime:
    __init__() = global mystdout = Base.stdout #= also works =#
    ```

Se imponen varias restricciones adicionales a las operaciones que se pueden realizar al precompilar código para ayudar al usuario a evitar otras situaciones de comportamiento incorrecto:

1. Llamando a [`eval`](@ref) para causar un efecto secundario en otro módulo. Esto también provocará que se emita una advertencia cuando se active la bandera de precompilación incremental.
2. `global const` declaraciones desde el ámbito local después de que `__init__()` ha comenzado (ver el problema #12010 para planes de agregar un error para esto)
3. Reemplazar un módulo es un error de tiempo de ejecución al realizar una precompilación incremental.

Algunos otros puntos a tener en cuenta:

1. No se realiza recarga de código / invalidación de caché después de que se realizan cambios en los archivos fuente, (incluyendo por `Pkg.update`), y no se realiza limpieza después de `Pkg.rm`
2. El comportamiento de compartición de memoria de un arreglo remodelado es ignorado por la precompilación (cada vista obtiene su propia copia)
3. Se espera que el sistema de archivos no cambie entre el tiempo de compilación y el tiempo de ejecución, por ejemplo, [`@__FILE__`](@ref)/`source_path()` para encontrar recursos en tiempo de ejecución, o el macro `@checked_lib` de BinDeps. A veces esto es inevitable. Sin embargo, cuando sea posible, puede ser una buena práctica copiar recursos en el módulo en el tiempo de compilación para que no necesiten ser encontrados en tiempo de ejecución.
4. Los objetos `WeakRef` y los finalizadores no se manejan actualmente de manera adecuada por el serializador (esto se solucionará en una próxima versión).
5. Por lo general, es mejor evitar capturar referencias a instancias de objetos de metadatos internos como `Method`, `MethodInstance`, `MethodTable`, `TypeMapLevel`, `TypeMapEntry` y campos de esos objetos, ya que esto puede confundir al serializador y puede no llevar al resultado que deseas. No es necesariamente un error hacerlo, pero simplemente debes estar preparado para que el sistema intente copiar algunos de estos y crear una única instancia única de otros.

A veces es útil durante el desarrollo de módulos desactivar la precompilación incremental. La opción de línea de comandos `--compiled-modules={yes|no|existing}` te permite activar y desactivar la precompilación de módulos. Cuando Julia se inicia con `--compiled-modules=no`, los módulos serializados en la caché de compilación se ignoran al cargar módulos y dependencias de módulos. En algunos casos, es posible que desees cargar módulos precompilados existentes, pero no crear nuevos. Esto se puede hacer iniciando Julia con `--compiled-modules=existing`. Un control más detallado está disponible con `--pkgimages={yes|no|existing}`, que solo afecta el almacenamiento de código nativo durante la precompilación. `Base.compilecache` aún se puede llamar manualmente. El estado de esta opción de línea de comandos se pasa a `Pkg.build` para desactivar la activación automática de la precompilación al instalar, actualizar y construir explícitamente paquetes.

También puedes depurar algunos fallos de precompilación con variables de entorno. Establecer `JULIA_VERBOSE_LINKING=true` puede ayudar a resolver fallos en el enlace de bibliotecas compartidas de código nativo compilado. Consulta la parte de **Documentación para Desarrolladores** del manual de Julia, donde encontrarás más detalles en la sección que documenta los internos de Julia bajo "Imágenes de Paquete".
