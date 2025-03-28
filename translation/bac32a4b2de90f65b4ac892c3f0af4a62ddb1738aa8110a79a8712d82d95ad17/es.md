# Frequently Asked Questions

## General

### Is Julia named after someone or something?

No.

### Why don't you compile Matlab/Python/R/… code to Julia?

Dado que muchas personas están familiarizadas con la sintaxis de otros lenguajes dinámicos, y ya se ha escrito mucho código en esos lenguajes, es natural preguntarse por qué no simplemente conectamos un front-end de Matlab o Python a un back-end de Julia (o “transpilamos” código a Julia) para obtener todos los beneficios de rendimiento de Julia sin requerir que los programadores aprendan un nuevo lenguaje. Sencillo, ¿verdad?

El problema básico es que no hay *nada especial en el compilador de Julia*: utilizamos un compilador común (LLVM) sin “ingredientes secretos” que otros desarrolladores de lenguajes no conozcan. De hecho, el compilador de Julia es en muchos aspectos mucho más simple que los de otros lenguajes dinámicos (por ejemplo, PyPy o LuaJIT). La ventaja de rendimiento de Julia proviene casi en su totalidad de su front-end: su semántica de lenguaje permite que un [well-written Julia program](@ref man-performance-tips) *ofrezca más oportunidades al compilador* para generar código y disposiciones de memoria eficientes. Si intentaras compilar código de Matlab o Python a Julia, nuestro compilador estaría limitado por la semántica de Matlab o Python para producir un código no mejor que el de los compiladores existentes para esos lenguajes (y probablemente peor). El papel clave de la semántica es también la razón por la que varios compiladores de Python existentes (como Numba y Pythran) solo intentan optimizar un pequeño subconjunto del lenguaje (por ejemplo, operaciones en arreglos y escalares de Numpy), y para este subconjunto ya están haciendo al menos tan bien como podríamos hacerlo para la misma semántica. Las personas que trabajan en esos proyectos son increíblemente inteligentes y han logrado cosas asombrosas, pero adaptar un compilador a un lenguaje que fue diseñado para ser interpretado es un problema muy difícil.

La ventaja de Julia es que un buen rendimiento no se limita a un pequeño subconjunto de tipos y operaciones "integrados", y se puede escribir código genérico de alto nivel que funcione con tipos definidos por el usuario arbitrarios mientras se mantiene rápido y eficiente en memoria. Los tipos en lenguajes como Python simplemente no proporcionan suficiente información al compilador para capacidades similares, por lo que tan pronto como usas esos lenguajes como un front-end de Julia, te quedarías atascado.

Por razones similares, la traducción automatizada a Julia también generaría típicamente código ilegible, lento y no idiomático que no sería un buen punto de partida para un puerto nativo de Julia desde otro lenguaje.

Por otro lado, la *interoperabilidad* del lenguaje es extremadamente útil: ¡queremos aprovechar el código existente de alta calidad en otros lenguajes desde Julia (y viceversa)! La mejor manera de habilitar esto no es un transpiler, sino a través de instalaciones de llamada inter-lenguaje fáciles. Hemos trabajado arduamente en esto, desde el intrínseco `ccall` incorporado (para llamar a bibliotecas de C y Fortran) hasta los paquetes [JuliaInterop](https://github.com/JuliaInterop) que conectan Julia con Python, Matlab, C++ y más.

## [Public API](@id man-api)

### How does Julia define its public API?

La [API](https://en.wikipedia.org/wiki/API) pública de Julia es el comportamiento descrito en la documentación de los símbolos públicos de `Base` y las bibliotecas estándar. Las funciones, tipos y constantes no son parte de la API pública si no son públicas, incluso si tienen docstrings o están descritas en la documentación. Además, solo el comportamiento documentado de los símbolos públicos es parte de la API pública. El comportamiento no documentado de los símbolos públicos es interno.

Los símbolos públicos son aquellos marcados con `public foo` o `export foo`.

En otras palabras:

  * El comportamiento documentado de los símbolos públicos es parte de la API pública.
  * El comportamiento no documentado de los símbolos públicos no es parte de la API pública.
  * El comportamiento documentado de los símbolos privados no es parte de la API pública.
  * El comportamiento no documentado de los símbolos privados no es parte de la API pública.

Puedes obtener una lista completa de los símbolos públicos de un módulo con `names(MyModule)`.

Se anima a los autores de paquetes a definir su API pública de manera similar.

Cualquier cosa en la API pública de Julia está cubierta por [SemVer](https://semver.org/) y, por lo tanto, no será eliminada ni recibirá cambios significativos antes de Julia 2.0.

### There is a useful undocumented function/type/constant. Can I use it?

Updating Julia may break your code if you use non-public API.  If the code is self-contained, it may be a good idea to copy it into your project.  If you want to rely on a complex non-public API, especially when using it from a stable package, it is a good idea to open an [issue](https://github.com/JuliaLang/julia/issues) or [pull request](https://github.com/JuliaLang/julia/pulls) to start a discussion for turning it into a public API.  However, we do not discourage the attempt to create packages that expose stable public interfaces while relying on non-public implementation details of Julia and buffering the differences across different Julia versions.

### The documentation is not accurate enough. Can I rely on the existing behavior?

Por favor, abre un [issue](https://github.com/JuliaLang/julia/issues) o [pull request](https://github.com/JuliaLang/julia/pulls) para comenzar una discusión sobre la transformación del comportamiento existente en una API pública.

## Sessions and the REPL

### How do I delete an object in memory?

Julia no tiene un análogo de la función `clear` de MATLAB; una vez que un nombre está definido en una sesión de Julia (técnicamente, en el módulo `Main`), siempre está presente.

Si el uso de memoria es tu preocupación, siempre puedes reemplazar objetos por otros que consuman menos memoria. Por ejemplo, si `A` es un arreglo del tamaño de un gigabyte que ya no necesitas, puedes liberar la memoria con `A = nothing`. La memoria se liberará la próxima vez que se ejecute el recolector de basura; puedes forzar que esto suceda con [`GC.gc()`](@ref Base.GC.gc). Además, un intento de usar `A` probablemente resultará en un error, porque la mayoría de los métodos no están definidos en el tipo `Nothing`.

### How can I modify the declaration of a type in my session?

Quizás has definido un tipo y luego te das cuenta de que necesitas agregar un nuevo campo. Si intentas esto en el REPL, obtienes el error:

```
ERROR: invalid redefinition of constant MyType
```

Los tipos en el módulo `Main` no se pueden redefinir.

Mientras que esto puede ser inconveniente cuando estás desarrollando nuevo código, hay una excelente solución alternativa. Los módulos pueden ser reemplazados redefiniéndolos, y así, si envuelves todo tu nuevo código dentro de un módulo, puedes redefinir tipos y constantes. No puedes importar los nombres de tipo en `Main` y luego esperar poder redefinirlos allí, pero puedes usar el nombre del módulo para resolver el alcance. En otras palabras, mientras desarrollas, podrías usar un flujo de trabajo algo como esto:

```julia
include("mynewcode.jl")              # this defines a module MyModule
obj1 = MyModule.ObjConstructor(a, b)
obj2 = MyModule.somefunction(obj1)
# Got an error. Change something in "mynewcode.jl"
include("mynewcode.jl")              # reload the module
obj1 = MyModule.ObjConstructor(a, b) # old objects are no longer valid, must reconstruct
obj2 = MyModule.somefunction(obj1)   # this time it worked!
obj3 = MyModule.someotherfunction(obj2, c)
...
```

## [Scripting](@id man-scripting)

### How do I check if the current file is being run as the main script?

Cuando un archivo se ejecuta como el script principal usando `julia file.jl`, uno podría querer activar funcionalidades adicionales como el manejo de argumentos de línea de comandos. Una forma de determinar que un archivo se ejecuta de esta manera es verificar si `abspath(PROGRAM_FILE) == @__FILE__` es `true`.

Sin embargo, se recomienda no escribir archivos que funcionen tanto como un script como una biblioteca importable. Si se necesita funcionalidad disponible tanto como una biblioteca como un script, es mejor escribirla como una biblioteca y luego importar la funcionalidad en un script distinto.

### [How do I catch CTRL-C in a script?](@id catch-ctrl-c)

Ejecutar un script de Julia usando `julia file.jl` no lanza [`InterruptException`](@ref) cuando intentas terminarlo con CTRL-C (SIGINT). Para ejecutar un cierto código antes de terminar un script de Julia, que puede o no ser causado por CTRL-C, usa [`atexit`](@ref). Alternativamente, puedes usar `julia -e 'include(popfirst!(ARGS))' file.jl` para ejecutar un script mientras puedes capturar `InterruptException` en el bloque [`try`](@ref). Ten en cuenta que con esta estrategia [`PROGRAM_FILE`](@ref) no se establecerá.

### How do I pass options to `julia` using `#!/usr/bin/env`?

Pasar opciones a `julia` en una línea shebang, como en `#!/usr/bin/env julia --startup-file=no`, no funcionará en muchas plataformas (BSD, macOS, Linux) donde el núcleo, a diferencia de la shell, no divide los argumentos en caracteres de espacio. La opción `env -S`, que divide una cadena de argumento única en múltiples argumentos en los espacios, similar a una shell, ofrece una solución simple:

```julia
#!/usr/bin/env -S julia --color=yes --startup-file=no
@show ARGS  # put any Julia code here
```

!!! note
    La opción `env -S` apareció en FreeBSD 6.0 (2005), macOS Sierra (2016) y GNU/Linux coreutils 8.30 (2018).


### Why doesn't `run` support `*` or pipes for scripting external programs?

La función [`run`](@ref) de Julia lanza programas externos *directamente*, sin invocar un [operating-system shell](https://en.wikipedia.org/wiki/Shell_(computing)) (a diferencia de la función `system("...")` en otros lenguajes como Python, R o C). Eso significa que `run` no realiza la expansión de comodines de `*` (["globbing"](https://en.wikipedia.org/wiki/Glob_(programming))), ni interpreta [shell pipelines](https://en.wikipedia.org/wiki/Pipeline_(Unix)) como `|` o `>`.

Aún puedes hacer globbing y tuberías utilizando las características de Julia, sin embargo. Por ejemplo, la función incorporada [`pipeline`](@ref) te permite encadenar programas y archivos externos, similar a las tuberías de shell, y el [Glob.jl package](https://github.com/vtjnash/Glob.jl) implementa globbing compatible con POSIX.

Puedes, por supuesto, ejecutar programas a través de la shell pasando explícitamente una shell y una cadena de comando a `run`, por ejemplo, ```run(`sh -c "ls > files.txt"`)``` para usar el Unix [Bourne shell](https://en.wikipedia.org/wiki/Bourne_shell), pero generalmente deberías preferir la escritura en Julia pura como ```run(pipeline(`ls`, "files.txt"))```. La razón por la que evitamos la shell por defecto es que [shelling out sucks](https://julialang.org/blog/2012/03/shelling-out-sucks/): lanzar procesos a través de la shell es lento, frágil ante la cita de caracteres especiales, tiene un manejo de errores deficiente y es problemático para la portabilidad. (Los desarrolladores de Python llegaron a un [similar conclusion](https://www.python.org/dev/peps/pep-0324/#motivation).)

## Variables and Assignments

### Why am I getting `UndefVarError` from a simple loop?

Podrías tener algo como:

```
x = 0
while x < 10
    x += 1
end
```

y nota que funciona bien en un entorno interactivo (como el REPL de Julia), pero da ```UndefVarError: `x` no definido``` cuando intentas ejecutarlo en un script u otro archivo. Lo que está sucediendo es que Julia generalmente requiere que **seas explícito sobre la asignación a variables globales en un ámbito local**.

Aquí, `x` es una variable global, `while` define un [local scope](@ref scope-of-variables), y `x += 1` es una asignación a una global en ese ámbito local.

Como se mencionó anteriormente, Julia (versión 1.5 o posterior) te permite omitir la palabra clave `global` para el código en el REPL (y muchos otros entornos interactivos), para simplificar la exploración (por ejemplo, copiar y pegar código de una función para ejecutarlo de forma interactiva). Sin embargo, una vez que te mueves al código en archivos, Julia requiere un enfoque más disciplinado para las variables globales. Tienes al menos tres opciones:

1. Coloca el código en una función (para que `x` sea una variable *local* en una función). En general, es una buena ingeniería de software usar funciones en lugar de scripts globales (busca en línea "por qué las variables globales son malas" para ver muchas explicaciones). En Julia, las variables globales también son [slow](@ref man-performance-tips).
2. Envuelve el código en un bloque [`let`](@ref). (Esto hace que `x` sea una variable local dentro de la declaración `let ... end`, eliminando nuevamente la necesidad de `global`).
3. Marque explícitamente `x` como `global` dentro del ámbito local antes de asignarle un valor, por ejemplo, escriba `global x += 1`.

Más información se puede encontrar en la sección del manual [on soft scope](@ref on-soft-scope).

## Functions

### I passed an argument `x` to a function, modified it inside that function, but on the outside, the variable `x` is still unchanged. Why?

Supongamos que llamas a una función así:

```jldoctest
julia> x = 10
10

julia> function change_value!(y)
           y = 17
       end
change_value! (generic function with 1 method)

julia> change_value!(x)
17

julia> x # x is unchanged!
10
```

En Julia, el enlace de una variable `x` no puede ser cambiado al pasar `x` como argumento a una función. Al llamar a `change_value!(x)` en el ejemplo anterior, `y` es una variable recién creada, inicialmente vinculada al valor de `x`, es decir, `10`; luego `y` se vuelve a vincular a la constante `17`, mientras que la variable `x` del ámbito exterior queda sin tocar.

Sin embargo, si `x` está vinculado a un objeto de tipo `Array` (o cualquier otro tipo *mutable*). Desde dentro de la función, no puedes "desvincular" `x` de este Array, pero *puedes* cambiar su contenido. Por ejemplo:

```jldoctest
julia> x = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> function change_array!(A)
           A[1] = 5
       end
change_array! (generic function with 1 method)

julia> change_array!(x)
5

julia> x
3-element Vector{Int64}:
 5
 2
 3
```

Aquí creamos una función `change_array!`, que asigna `5` al primer elemento del array pasado (vinculado a `x` en el sitio de llamada, y vinculado a `A` dentro de la función). Nota que, después de la llamada a la función, `x` sigue vinculado al mismo array, pero el contenido de ese array cambió: las variables `A` y `x` eran vinculaciones distintas que se referían al mismo objeto `Array` mutable.

### Can I use `using` or `import` inside a function?

No, no se te permite tener una declaración `using` o `import` dentro de una función. Si deseas importar un módulo pero solo usar sus símbolos dentro de una función específica o un conjunto de funciones, tienes dos opciones:

1. Usa `import`:

    ```julia
    import Foo
    function bar(...)
        # ... refer to Foo symbols via Foo.baz ...
    end
    ```

    Esto carga el módulo `Foo` y define una variable `Foo` que se refiere al módulo, pero no importa ninguno de los otros símbolos del módulo en el espacio de nombres actual. Te refieres a los símbolos de `Foo` por sus nombres calificados `Foo.bar`, etc.
2. Envuelve tu función en un módulo:

    ```julia
    module Bar
    export bar
    using Foo
    function bar(...)
        # ... refer to Foo.baz as simply baz ....
    end
    end
    using Bar
    ```

    Esto importa todos los símbolos de `Foo`, pero solo dentro del módulo `Bar`.

### What does the `...` operator do?

#### The two uses of the `...` operator: slurping and splatting

Muchos recién llegados a Julia encuentran confuso el uso del operador `...`. Parte de lo que hace que el operador `...` sea confuso es que significa dos cosas diferentes dependiendo del contexto.

#### `...` combines many arguments into one argument in function definitions

En el contexto de las definiciones de funciones, el operador `...` se utiliza para combinar muchos argumentos diferentes en un solo argumento. Este uso de `...` para combinar muchos argumentos diferentes en un solo argumento se llama slurping:

```jldoctest
julia> function printargs(args...)
           println(typeof(args))
           for (i, arg) in enumerate(args)
               println("Arg #$i = $arg")
           end
       end
printargs (generic function with 1 method)

julia> printargs(1, 2, 3)
Tuple{Int64, Int64, Int64}
Arg #1 = 1
Arg #2 = 2
Arg #3 = 3
```

Si Julia fuera un lenguaje que hiciera un uso más liberal de los caracteres ASCII, el operador de slurping podría haberse escrito como `<-...` en lugar de `...`.

#### `...` splits one argument into many different arguments in function calls

En contraste con el uso del operador `...` para denotar la agrupación de muchos argumentos diferentes en un solo argumento al definir una función, el operador `...` también se utiliza para hacer que un solo argumento de función se divida en muchos argumentos diferentes cuando se usa en el contexto de una llamada a función. Este uso de `...` se llama splatting:

```jldoctest
julia> function threeargs(a, b, c)
           println("a = $a::$(typeof(a))")
           println("b = $b::$(typeof(b))")
           println("c = $c::$(typeof(c))")
       end
threeargs (generic function with 1 method)

julia> x = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> threeargs(x...)
a = 1::Int64
b = 2::Int64
c = 3::Int64
```

Si Julia fuera un lenguaje que hiciera un uso más liberal de los caracteres ASCII, el operador de splatting podría haberse escrito como `...->` en lugar de `...`.

### What is the return value of an assignment?

El operador `=` siempre devuelve el lado derecho, por lo tanto:

```jldoctest
julia> function threeint()
           x::Int = 3.0
           x # returns variable x
       end
threeint (generic function with 1 method)

julia> function threefloat()
           x::Int = 3.0 # returns 3.0
       end
threefloat (generic function with 1 method)

julia> threeint()
3

julia> threefloat()
3.0
```

y de manera similar:

```jldoctest
julia> function twothreetup()
           x, y = [2, 3] # assigns 2 to x and 3 to y
           x, y # returns a tuple
       end
twothreetup (generic function with 1 method)

julia> function twothreearr()
           x, y = [2, 3] # returns an array
       end
twothreearr (generic function with 1 method)

julia> twothreetup()
(2, 3)

julia> twothreearr()
2-element Vector{Int64}:
 2
 3
```

## Types, type declarations, and constructors

### [What does "type-stable" mean?](@id man-type-stability)

Significa que el tipo de la salida es predecible a partir de los tipos de las entradas. En particular, significa que el tipo de la salida no puede variar dependiendo de los *valores* de las entradas. El siguiente código *no* es estable en cuanto al tipo:

```jldoctest
julia> function unstable(flag::Bool)
           if flag
               return 1
           else
               return 1.0
           end
       end
unstable (generic function with 1 method)
```

Devuelve ya sea un `Int` o un [`Float64`](@ref) dependiendo del valor de su argumento. Dado que Julia no puede predecir el tipo de retorno de esta función en tiempo de compilación, cualquier cálculo que la utilice debe ser capaz de manejar valores de ambos tipos, lo que dificulta la producción de código máquina rápido.

### [Why does Julia give a `DomainError` for certain seemingly-sensible operations?](@id faq-domain-errors)

Ciertas operaciones tienen sentido matemático pero resultan en errores:

```jldoctest
julia> sqrt(-2.0)
ERROR: DomainError with -2.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

Este comportamiento es una consecuencia inconveniente del requisito de estabilidad de tipo. En el caso de [`sqrt`](@ref), la mayoría de los usuarios quiere que `sqrt(2.0)` devuelva un número real, y estarían descontentos si produjera el número complejo `1.4142135623730951 + 0.0im`. Se podría escribir la función `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` para cambiar a una salida de valor complejo solo cuando se le pase un número negativo (que es lo que hace `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` en algunos otros lenguajes), pero entonces el resultado no sería [type-stable](@ref man-type-stability) y la función `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` tendría un rendimiento deficiente.

En estos y otros casos, puedes obtener el resultado que deseas eligiendo un *tipo de entrada* que transmita tu disposición a aceptar un *tipo de salida* en el que el resultado pueda ser representado:

```jldoctest
julia> sqrt(-2.0+0im)
0.0 + 1.4142135623730951im
```

### How can I constrain or compute type parameters?

Los parámetros de un [parametric type](@ref Parametric-Types) pueden contener valores de tipos o bits, y el tipo en sí elige cómo utiliza estos parámetros. Por ejemplo, `Array{Float64, 2}` está parametrizado por el tipo `Float64` para expresar su tipo de elemento y el valor entero `2` para expresar su número de dimensiones. Al definir tu propio tipo paramétrico, puedes usar restricciones de subtipo para declarar que un cierto parámetro debe ser un subtipo ([`<:`](@ref)) de algún tipo abstracto o un parámetro de tipo anterior. Sin embargo, no hay una sintaxis dedicada para declarar que un parámetro debe ser un *valor* de un tipo dado; es decir, no puedes declarar directamente que un parámetro de dimensionalidad [`isa`](@ref) `Int` dentro de la definición de `struct`, por ejemplo. De manera similar, no puedes realizar cálculos (incluyendo cosas simples como suma o resta) sobre parámetros de tipo. En cambio, estos tipos de restricciones y relaciones pueden expresarse a través de parámetros de tipo adicionales que se calculan y se imponen dentro de la [constructors](@ref man-constructors) del tipo.

Como ejemplo, considera

```julia
struct ConstrainedType{T,N,N+1} # NOTE: INVALID SYNTAX
    A::Array{T,N}
    B::Array{T,N+1}
end
```

donde el usuario desearía hacer cumplir que el tercer parámetro de tipo sea siempre el segundo más uno. Esto se puede implementar con un parámetro de tipo explícito que se verifica mediante un [inner constructor method](@ref man-inner-constructor-methods) (donde se puede combinar con otras verificaciones):

```julia
struct ConstrainedType{T,N,M}
    A::Array{T,N}
    B::Array{T,M}
    function ConstrainedType(A::Array{T,N}, B::Array{T,M}) where {T,N,M}
        N + 1 == M || throw(ArgumentError("second argument should have one more axis" ))
        new{T,N,M}(A, B)
    end
end
```

Esta verificación es generalmente *sin costo*, ya que el compilador puede omitir la verificación de tipos concretos válidos. Si el segundo argumento también se calcula, puede ser ventajoso proporcionar un [outer constructor method](@ref man-outer-constructor-methods) que realice este cálculo:

```julia
ConstrainedType(A) = ConstrainedType(A, compute_B(A))
```

### [Why does Julia use native machine integer arithmetic?](@id faq-integer-arithmetic)

Julia utiliza aritmética de máquina para cálculos enteros. Esto significa que el rango de valores `Int` está limitado y se envuelve en ambos extremos, de modo que sumar, restar y multiplicar enteros puede desbordarse o subdesbordarse, lo que puede llevar a algunos resultados que pueden ser desconcertantes al principio:

```jldoctest
julia> x = typemax(Int)
9223372036854775807

julia> y = x+1
-9223372036854775808

julia> z = -y
-9223372036854775808

julia> 2*z
0
```

Claramente, esto está lejos de la forma en que se comportan los enteros matemáticos, y podrías pensar que es menos que ideal que un lenguaje de programación de alto nivel exponga esto al usuario. Sin embargo, para trabajos numéricos donde la eficiencia y la transparencia son primordiales, las alternativas son peores.

Una alternativa a considerar sería verificar cada operación entera para detectar desbordamiento y promover los resultados a tipos de enteros más grandes como [`Int128`](@ref) o [`BigInt`](@ref) en caso de desbordamiento. Desafortunadamente, esto introduce una sobrecarga importante en cada operación entera (piensa en incrementar un contador de bucle): requiere emitir código para realizar verificaciones de desbordamiento en tiempo de ejecución después de las instrucciones aritméticas y ramificaciones para manejar posibles desbordamientos. Peor aún, esto causaría que cada cálculo que involucre enteros sea inestable en cuanto a tipos. Como mencionamos anteriormente, [type-stability is crucial](@ref man-type-stability) para la generación efectiva de código eficiente. Si no puedes contar con que los resultados de las operaciones enteras sean enteros, es imposible generar código rápido y simple de la manera en que lo hacen los compiladores de C y Fortran.

Una variación de este enfoque, que evita la apariencia de inestabilidad de tipo, es fusionar los tipos `Int` y [`BigInt`](@ref) en un único tipo de entero híbrido, que internamente cambia de representación cuando un resultado ya no cabe en el tamaño de un entero de máquina. Si bien esto superficialmente evita la inestabilidad de tipo a nivel de código Julia, simplemente barre el problema debajo de la alfombra al imponer todas las mismas dificultades al código C que implementa este tipo de entero híbrido. Este enfoque *puede* hacerse funcionar e incluso puede hacerse bastante rápido en muchos casos, pero tiene varias desventajas. Un problema es que la representación en memoria de enteros y arreglos de enteros ya no coincide con la representación natural utilizada por C, Fortran y otros lenguajes con enteros de máquina nativos. Por lo tanto, para interoperar con esos lenguajes, en última instancia tendríamos que introducir tipos de enteros nativos de todos modos. Cualquier representación no acotada de enteros no puede tener un número fijo de bits, y por lo tanto no puede almacenarse en línea en un arreglo con espacios de tamaño fijo; los valores enteros grandes siempre requerirán almacenamiento separado en el montón. Y, por supuesto, no importa cuán ingeniosa sea la implementación de un entero híbrido, siempre hay trampas de rendimiento: situaciones donde el rendimiento se degrada inesperadamente. La representación compleja, la falta de interoperabilidad con C y Fortran, la incapacidad de representar arreglos de enteros sin almacenamiento adicional en el montón, y las características de rendimiento impredecibles hacen que incluso las implementaciones de enteros híbridos más ingeniosas sean una mala elección para trabajos numéricos de alto rendimiento.

Una alternativa al uso de enteros híbridos o la promoción a BigInts es utilizar aritmética entera de saturación, donde sumar al valor entero más grande lo deja sin cambios y de igual manera al restar del valor entero más pequeño. Esto es precisamente lo que hace Matlab™:

```
>> int64(9223372036854775807)

ans =

  9223372036854775807

>> int64(9223372036854775807) + 1

ans =

  9223372036854775807

>> int64(-9223372036854775808)

ans =

 -9223372036854775808

>> int64(-9223372036854775808) - 1

ans =

 -9223372036854775808
```

A primera vista, esto parece razonable ya que 9223372036854775807 está mucho más cerca de 9223372036854775808 que -9223372036854775808 y los enteros todavía se representan con un tamaño fijo de una manera natural que es compatible con C y Fortran. Sin embargo, la aritmética entera saturada es profundamente problemática. El primer y más obvio problema es que esta no es la forma en que funciona la aritmética entera de la máquina, por lo que implementar operaciones saturadas requiere emitir instrucciones después de cada operación entera de la máquina para verificar desbordamientos o subdesbordamientos y reemplazar el resultado con [`typemin(Int)`](@ref) o [`typemax(Int)`](@ref) según corresponda. Esto por sí solo expande cada operación entera de una sola instrucción rápida a media docena de instrucciones, probablemente incluyendo ramas. Vaya. Pero se pone peor: la aritmética entera saturada no es asociativa. Considera este cálculo en Matlab:

```
>> n = int64(2)^62
4611686018427387904

>> n + (n - 1)
9223372036854775807

>> (n + n) - 1
9223372036854775806
```

Esto dificulta la escritura de muchos algoritmos básicos de enteros, ya que muchas técnicas comunes dependen del hecho de que la suma de máquina con desbordamiento *es* asociativa. Considera encontrar el punto medio entre los valores enteros `lo` y `hi` en Julia utilizando la expresión `(lo + hi) >>> 1`:

```jldoctest
julia> n = 2^62
4611686018427387904

julia> (n + 2n) >>> 1
6917529027641081856
```

¿Ves? No hay problema. Ese es el punto medio correcto entre 2^62 y 2^63, a pesar del hecho de que `n + 2n` es -4611686018427387904. Ahora inténtalo en Matlab:

```
>> (n + 2*n)/2

ans =

  4611686018427387904
```

Oops. Agregar un operador `>>>` a Matlab no ayudaría, porque la saturación que ocurre al sumar `n` y `2n` ya ha destruido la información necesaria para calcular el punto medio correcto.

No solo la falta de asociatividad es desafortunada para los programadores que no pueden confiar en ella para técnicas como esta, sino que también frustra casi cualquier cosa que los compiladores puedan querer hacer para optimizar la aritmética entera. Por ejemplo, dado que los enteros de Julia utilizan la aritmética entera normal de la máquina, LLVM puede optimizar agresivamente funciones simples como `f(k) = 5k-1`. El código de máquina para esta función es solo esto:

```julia-repl
julia> code_native(f, Tuple{Int})
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 1
  leaq  -1(%rdi,%rdi,4), %rax
  popq  %rbp
  retq
  nopl  (%rax,%rax)
```

El cuerpo real de la función es una única instrucción `leaq`, que calcula la multiplicación entera y la suma a la vez. Esto es aún más beneficioso cuando `f` se inserta en otra función:

```julia-repl
julia> function g(k, n)
           for i = 1:n
               k = f(k)
           end
           return k
       end
g (generic function with 1 methods)

julia> code_native(g, Tuple{Int,Int})
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 2
  testq %rsi, %rsi
  jle L26
  nopl  (%rax)
Source line: 3
L16:
  leaq  -1(%rdi,%rdi,4), %rdi
Source line: 2
  decq  %rsi
  jne L16
Source line: 5
L26:
  movq  %rdi, %rax
  popq  %rbp
  retq
  nop
```

Dado que la llamada a `f` se inserta en línea, el cuerpo del bucle termina siendo solo una única instrucción `leaq`. A continuación, considera lo que sucede si fijamos el número de iteraciones del bucle:

```julia-repl
julia> function g(k)
           for i = 1:10
               k = f(k)
           end
           return k
       end
g (generic function with 2 methods)

julia> code_native(g,(Int,))
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 3
  imulq $9765625, %rdi, %rax    # imm = 0x9502F9
  addq  $-2441406, %rax         # imm = 0xFFDABF42
Source line: 5
  popq  %rbp
  retq
  nopw  %cs:(%rax,%rax)
```

Porque el compilador sabe que la adición y la multiplicación de enteros son asociativas y que la multiplicación se distribuye sobre la adición, - ninguna de las cuales es cierta en la aritmética saturada - puede optimizar todo el bucle a solo una multiplicación y una suma. La aritmética saturada derrota completamente este tipo de optimización, ya que la asociatividad y la distributividad pueden fallar en cada iteración del bucle, causando diferentes resultados dependiendo de en qué iteración ocurre la falla. El compilador puede desenrollar el bucle, pero no puede reducir algebraicamente múltiples operaciones en menos operaciones equivalentes.

La alternativa más razonable a tener aritmética entera que se desborde silenciosamente es hacer aritmética verificada en todas partes, generando errores cuando las sumas, restas y multiplicaciones se desbordan, produciendo valores que no son correctos. En este [blog post](https://danluu.com/integer-overflow/), Dan Luu analiza esto y encuentra que, en lugar del costo trivial que este enfoque debería tener en teoría, termina teniendo un costo sustancial debido a que los compiladores (LLVM y GCC) no optimizan de manera eficiente alrededor de las verificaciones de desbordamiento añadidas. Si esto mejora en el futuro, podríamos considerar establecer la aritmética entera verificada como predeterminada en Julia, pero por ahora, tenemos que vivir con la posibilidad de desbordamiento.

Mientras tanto, las operaciones de enteros seguras contra desbordamientos se pueden lograr mediante el uso de bibliotecas externas como [SaferIntegers.jl](https://github.com/JeffreySarnoff/SaferIntegers.jl). Tenga en cuenta que, como se mencionó anteriormente, el uso de estas bibliotecas aumenta significativamente el tiempo de ejecución del código que utiliza los tipos de enteros verificados. Sin embargo, para un uso limitado, esto es mucho menos problemático que si se utilizara para todas las operaciones de enteros. Puede seguir el estado de la discusión [here](https://github.com/JuliaLang/julia/issues/855).

### What are the possible causes of an `UndefVarError` during remote execution?

Como indica el error, una causa inmediata de un `UndefVarError` en un nodo remoto es que no existe una vinculación con ese nombre. Exploremos algunas de las posibles causas.

```julia-repl
julia> module Foo
           foo() = remotecall_fetch(x->x, 2, "Hello")
       end

julia> Foo.foo()
ERROR: On worker 2:
UndefVarError: `Foo` not defined in `Main`
Stacktrace:
[...]
```

El cierre `x->x` lleva una referencia a `Foo`, y dado que `Foo` no está disponible en el nodo 2, se lanza un `UndefVarError`.

Los globales bajo módulos que no sean `Main` no se serializan por valor al nodo remoto. Solo se envía una referencia. Las funciones que crean enlaces globales (excepto bajo `Main`) pueden causar que se lance un `UndefVarError` más tarde.

```julia-repl
julia> @everywhere module Foo
           function foo()
               global gvar = "Hello"
               remotecall_fetch(()->gvar, 2)
           end
       end

julia> Foo.foo()
ERROR: On worker 2:
UndefVarError: `gvar` not defined in `Main.Foo`
Stacktrace:
[...]
```

En el ejemplo anterior, `@everywhere module Foo` definió `Foo` en todos los nodos. Sin embargo, la llamada a `Foo.foo()` creó un nuevo enlace global `gvar` en el nodo local, pero este no se encontró en el nodo 2, lo que resultó en un error `UndefVarError`.

Tenga en cuenta que esto no se aplica a los globales creados bajo el módulo `Main`. Los globales bajo el módulo `Main` se serializan y se crean nuevos enlaces bajo `Main` en el nodo remoto.

```julia-repl
julia> gvar_self = "Node1"
"Node1"

julia> remotecall_fetch(()->gvar_self, 2)
"Node1"

julia> remotecall_fetch(varinfo, 2)
name          size summary
––––––––– –––––––– –––––––
Base               Module
Core               Module
Main               Module
gvar_self 13 bytes String
```

Esto no se aplica a las declaraciones de `function` o `struct`. Sin embargo, las funciones anónimas vinculadas a variables globales se serializan como se puede ver a continuación.

```julia-repl
julia> bar() = 1
bar (generic function with 1 method)

julia> remotecall_fetch(bar, 2)
ERROR: On worker 2:
UndefVarError: `#bar` not defined in `Main`
[...]

julia> anon_bar  = ()->1
(::#21) (generic function with 1 method)

julia> remotecall_fetch(anon_bar, 2)
1
```

## Troubleshooting "method not matched": parametric type invariance and `MethodError`s

### Why doesn't it work to declare `foo(bar::Vector{Real}) = 42` and then call `foo([1])`?

Como verás si intentas esto, el resultado es un `MethodError`:

```jldoctest
julia> foo(x::Vector{Real}) = 42
foo (generic function with 1 method)

julia> foo([1])
ERROR: MethodError: no method matching foo(::Vector{Int64})
The function `foo` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  foo(!Matched::Vector{Real})
   @ Main none:1

Stacktrace:
[...]
```

Esto se debe a que `Vector{Real}` no es un supertipo de `Vector{Int}`. Puedes resolver este problema con algo como `foo(bar::Vector{T}) donde {T<:Real}` (o la forma corta `foo(bar::Vector{<:Real})` si el parámetro estático `T` no es necesario en el cuerpo de la función). El `T` es un comodín: primero especificas que debe ser un subtipo de Real, luego especificas que la función toma un Vector con elementos de ese tipo.

Este mismo problema se aplica a cualquier tipo compuesto `Comp`, no solo a `Vector`. Si `Comp` tiene un parámetro declarado del tipo `Y`, entonces otro tipo `Comp2` con un parámetro del tipo `X<:Y` no es un subtipo de `Comp`. Esta es la invariancia de tipo (en contraste, Tuple es covariante en sus parámetros). Consulta [Parametric Composite Types](@ref man-parametric-composite-types) para más explicaciones sobre esto.

### Why does Julia use `*` for string concatenation? Why not `+` or something else?

El [main argument](@ref man-concatenation) contra `+` es que la concatenación de cadenas no es conmutativa, mientras que `+` se utiliza generalmente como un operador conmutativo. Aunque la comunidad de Julia reconoce que otros lenguajes utilizan diferentes operadores y que `*` puede ser desconocido para algunos usuarios, comunica ciertas propiedades algebraicas.

Tenga en cuenta que también puede usar `string(...)` para concatenar cadenas (y otros valores convertidos a cadenas); de manera similar, `repeat` se puede usar en lugar de `^` para repetir cadenas. El [interpolation syntax](@ref string-interpolation) también es útil para construir cadenas.

## Packages and Modules

### What is the difference between "using" and "import"?

Hay varias diferencias entre `using` e `import` (ver [Modules section](https://docs.julialang.org/en/v1/manual/modules/#modules)), pero hay una diferencia importante que puede no parecer intuitiva a primera vista, y en la superficie (es decir, en términos de sintaxis) puede parecer muy menor. Al cargar módulos con `using`, necesitas decir `function Foo.bar(...` para extender la función `bar` del módulo `Foo` con un nuevo método, pero con `import Foo.bar`, solo necesitas decir `function bar(...` y automáticamente extiende la función `bar` del módulo `Foo`.

La razón por la que esto es lo suficientemente importante como para tener una sintaxis separada es que no quieres extender accidentalmente una función que no sabías que existía, porque eso podría causar fácilmente un error. Esto es más probable que ocurra con un método que toma un tipo común como una cadena o un entero, porque tanto tú como el otro módulo podrían definir un método para manejar dicho tipo común. Si usas `import`, entonces reemplazarás la implementación del otro módulo de `bar(s::AbstractString)` con tu nueva implementación, que podría hacer algo completamente diferente (y romper todas/muchas de las futuras utilizaciones de las otras funciones en el módulo Foo que dependen de llamar a bar).

## Nothingness and missing values

### [How does "null", "nothingness" or "missingness" work in Julia?](@id faq-nothing)

A diferencia de muchos lenguajes (por ejemplo, C y Java), los objetos de Julia no pueden ser "nulos" por defecto. Cuando una referencia (variable, campo de objeto o elemento de matriz) no está inicializada, acceder a ella generará inmediatamente un error. Esta situación se puede detectar utilizando las funciones [`isdefined`](@ref) o [`isassigned`](@ref Base.isassigned).

Algunas funciones se utilizan solo por sus efectos secundarios y no necesitan devolver un valor. En estos casos, la convención es devolver el valor `nothing`, que es solo un objeto singleton del tipo `Nothing`. Este es un tipo ordinario sin campos; no hay nada especial en él, excepto por esta convención, y que el REPL no imprime nada para él. Algunas construcciones del lenguaje que de otro modo no tendrían un valor también producen `nothing`, por ejemplo `if false; end`.

Para situaciones donde un valor `x` de tipo `T` existe solo a veces, se puede usar el tipo `Union{T, Nothing}` para argumentos de función, campos de objeto y tipos de elementos de matriz como el equivalente de [`Nullable`, `Option` or `Maybe`](https://en.wikipedia.org/wiki/Nullable_type) en otros lenguajes. Si el valor en sí puede ser `nothing` (notablemente, cuando `T` es `Any`), el tipo `Union{Some{T}, Nothing}` es más apropiado ya que `x == nothing` indica la ausencia de un valor, y `x == Some(nothing)` indica la presencia de un valor igual a `nothing`. La función [`something`](@ref) permite deshacer objetos `Some` y usar un valor predeterminado en lugar de argumentos `nothing`. Tenga en cuenta que el compilador puede generar código eficiente al trabajar con argumentos o campos `Union{T, Nothing}`.

Para representar datos faltantes en el sentido estadístico (`NA` en R o `NULL` en SQL), utiliza el objeto [`missing`](@ref). Consulta la sección [`Missing Values`](@ref missing) para más detalles.

En algunos lenguajes, la tupla vacía (`()`) se considera la forma canónica de la nada. Sin embargo, en julia es mejor pensar en ella como una tupla regular que contiene cero valores.

El tipo vacío (o "tipo inferior"), escrito como `Union{}` (un tipo de unión vacío), es un tipo sin valores y sin subtipos (excepto a sí mismo). Generalmente, no necesitarás usar este tipo.

## Memory

### Why does `x += y` allocate memory when `x` and `y` are arrays?

En Julia, `x += y` se reemplaza durante la reducción por `x = x + y`. Para los arreglos, esto tiene la consecuencia de que, en lugar de almacenar el resultado en la misma ubicación en memoria que `x`, se asigna un nuevo arreglo para almacenar el resultado. Si prefieres mutar `x`, usa `x .+= y` para actualizar cada elemento individualmente.

Aunque este comportamiento puede sorprender a algunos, la elección es deliberada. La razón principal es la presencia de objetos inmutables dentro de Julia, que no pueden cambiar su valor una vez creados. De hecho, un número es un objeto inmutable; las declaraciones `x = 5; x += 1` no modifican el significado de `5`, modifican el valor vinculado a `x`. Para un inmutable, la única forma de cambiar el valor es reasignarlo.

Para amplificar un poco más, considera la siguiente función:

```julia
function power_by_squaring(x, n::Int)
    ispow2(n) || error("This implementation only works for powers of 2")
    while n >= 2
        x *= x
        n >>= 1
    end
    x
end
```

Después de una llamada como `x = 5; y = power_by_squaring(x, 4)`, obtendrías el resultado esperado: `x == 5 && y == 625`. Sin embargo, supongamos que `*=`, cuando se usa con matrices, en su lugar muta el lado izquierdo. Habría dos problemas:

  * Para matrices cuadradas generales, `A = A*B` no se puede implementar sin almacenamiento temporal: `A[1,1]` se calcula y se almacena en el lado izquierdo antes de que termines de usarlo en el lado derecho.
  * Supongamos que estuvieras dispuesto a asignar un temporal para la computación (lo que eliminaría la mayor parte del sentido de hacer que `*=` funcione en su lugar); si aprovecharas la mutabilidad de `x`, entonces esta función se comportaría de manera diferente para entradas mutables e inmutables. En particular, para `x` inmutable, después de la llamada tendrías (en general) `y != x`, pero para `x` mutable tendrías `y == x`.

Porque se considera que apoyar la programación genérica es más importante que las posibles optimizaciones de rendimiento que se pueden lograr por otros medios (por ejemplo, utilizando broadcasting o bucles explícitos), operadores como `+=` y `*=` funcionan volviendo a enlazar nuevos valores.

## [Asynchronous IO and concurrent synchronous writes](@id faq-async-io)

### Why do concurrent writes to the same stream result in inter-mixed output?

Mientras que la API de I/O de streaming es sincrónica, la implementación subyacente es completamente asincrónica.

Por favor, proporciona el contenido en Markdown que deseas traducir.

```jldoctest
julia> @sync for i in 1:3
           @async write(stdout, string(i), " Foo ", " Bar ")
       end
123 Foo  Foo  Foo  Bar  Bar  Bar
```

Esto está sucediendo porque, aunque la llamada a `write` es sincrónica, la escritura de cada argumento cede a otras tareas mientras espera que esa parte de la E/S se complete.

`print` y `println` "bloquean" el flujo durante una llamada. En consecuencia, cambiar `write` a `println` en el ejemplo anterior resulta en:

```jldoctest
julia> @sync for i in 1:3
           @async println(stdout, string(i), " Foo ", " Bar ")
       end
1 Foo  Bar
2 Foo  Bar
3 Foo  Bar
```

Puedes bloquear tus escrituras con un `ReentrantLock` así:

```jldoctest
julia> l = ReentrantLock();

julia> @sync for i in 1:3
           @async begin
               lock(l)
               try
                   write(stdout, string(i), " Foo ", " Bar ")
               finally
                   unlock(l)
               end
           end
       end
1 Foo  Bar 2 Foo  Bar 3 Foo  Bar
```

## Arrays

### [What are the differences between zero-dimensional arrays and scalars?](@id faq-array-0dim)

Los arreglos de cero dimensiones son arreglos de la forma `Array{T,0}`. Se comportan de manera similar a los escalares, pero hay diferencias importantes. Merecen una mención especial porque son un caso especial que tiene sentido lógico dada la definición genérica de arreglos, pero puede ser un poco contraintuitivo al principio. La siguiente línea define un arreglo de cero dimensiones:

```
julia> A = zeros()
0-dimensional Array{Float64,0}:
0.0
```

En este ejemplo, `A` es un contenedor mutable que contiene un elemento, que se puede establecer con `A[] = 1.0` y recuperar con `A[]`. Todos los arreglos de cero dimensiones tienen el mismo tamaño (`size(A) == ()`) y longitud (`length(A) == 1`). En particular, los arreglos de cero dimensiones no están vacíos. Si encuentras esto poco intuitivo, aquí hay algunas ideas que pueden ayudar a entender la definición de Julia.

  * Los arreglos de cero dimensiones son el "punto" en comparación con la "línea" de un vector y el "plano" de una matriz. Así como una línea no tiene área (pero aún representa un conjunto de cosas), un punto no tiene longitud ni ninguna dimensión en absoluto (pero aún representa una cosa).
  * Definimos `prod(())` como 1, y el número total de elementos en un arreglo es el producto del tamaño. El tamaño de un arreglo de cero dimensiones es `()`, y por lo tanto su longitud es `1`.
  * Los arreglos de cero dimensiones no tienen nativamente ninguna dimensión en la que puedas indexar; son simplemente `A[]`. Podemos aplicar la misma regla de "uno final" para ellos como para todas las demás dimensionalidades de arreglos, por lo que de hecho puedes indexarlos como `A[1]`, `A[1,1]`, etc.; consulta [Omitted and extra indices](@ref).

También es importante entender las diferencias con los escalares ordinarios. Los escalares no son contenedores mutables (aunque son iterables y definen cosas como `length`, `getindex`, *p. ej.* `1[] == 1`). En particular, si `x = 0.0` se define como un escalar, es un error intentar cambiar su valor a través de `x[] = 1.0`. Un escalar `x` se puede convertir en un arreglo de cero dimensiones que lo contiene a través de `fill(x)`, y viceversa, un arreglo de cero dimensiones `a` se puede convertir en el escalar contenido a través de `a[]`. Otra diferencia es que un escalar puede participar en operaciones de álgebra lineal como `2 * rand(2,2)`, pero la operación análoga con un arreglo de cero dimensiones `fill(2) * rand(2,2)` es un error.

### Why are my Julia benchmarks for linear algebra operations different from other languages?

Es posible que encuentres que los benchmarks simples de bloques de construcción de álgebra lineal como

```julia
using BenchmarkTools
A = randn(1000, 1000)
B = randn(1000, 1000)
@btime $A \ $B
@btime $A * $B
```

puede ser diferente en comparación con otros lenguajes como Matlab o R.

Dado que operaciones como esta son envolturas muy delgadas sobre las funciones BLAS relevantes, la razón de la discrepancia es muy probable que sea

1. la biblioteca BLAS que cada lenguaje está utilizando,
2. el número de hilos concurrentes.

Julia compila y utiliza su propia copia de OpenBLAS, con hilos actualmente limitados a `8` (o el número de tus núcleos).

Modificar la configuración de OpenBLAS o compilar Julia con una biblioteca BLAS diferente, por ejemplo [Intel MKL](https://software.intel.com/en-us/mkl), puede proporcionar mejoras en el rendimiento. Puedes usar [MKL.jl](https://github.com/JuliaComputing/MKL.jl), un paquete que hace que el álgebra lineal de Julia use Intel MKL BLAS y LAPACK en lugar de OpenBLAS, o buscar en el foro de discusión sugerencias sobre cómo configurarlo manualmente. Ten en cuenta que Intel MKL no puede ser empaquetado con Julia, ya que no es de código abierto.

## Computing cluster

### How do I manage precompilation caches in distributed file systems?

Cuando se utiliza Julia en instalaciones de computación de alto rendimiento (HPC) con sistemas de archivos compartidos, se recomienda usar un depósito compartido (a través de la variable de entorno [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH)). Desde Julia v1.10, múltiples procesos de Julia en trabajadores funcionalmente similares y utilizando el mismo depósito coordinarán a través de bloqueos de pidfile para solo gastar esfuerzo en la precompilación en un proceso mientras los otros esperan. El proceso de precompilación indicará cuándo el proceso está precompilando o esperando a otro que está precompilando. Si no es interactivo, los mensajes son a través de `@debug`.

Sin embargo, debido a la caché del código binario, el rechazo de caché desde v1.9 es más estricto y los usuarios pueden necesitar establecer la variable de entorno [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) de manera adecuada para obtener una única caché que sea utilizable en todo el entorno HPC.

## Julia Releases

### Do I want to use the Stable, LTS, or nightly version of Julia?

La versión estable de Julia es la última versión lanzada de Julia, esta es la versión que la mayoría de las personas querrán ejecutar. Tiene las últimas características, incluyendo un rendimiento mejorado. La versión estable de Julia está versionada de acuerdo a [SemVer](https://semver.org/) como v1.x.y. Una nueva versión menor de Julia correspondiente a una nueva versión estable se realiza aproximadamente cada 4-5 meses después de unas semanas de pruebas como candidato a lanzamiento. A diferencia de la versión LTS, la versión estable normalmente no recibirá correcciones de errores después de que se haya lanzado otra versión estable de Julia. Sin embargo, actualizar a la siguiente versión estable siempre será posible, ya que cada versión de Julia v1.x seguirá ejecutando código escrito para versiones anteriores.

Puede que prefieras la versión LTS (Soporte a Largo Plazo) de Julia si buscas una base de código muy estable. La versión LTS actual de Julia está versionada según SemVer como v1.6.x; esta rama continuará recibiendo correcciones de errores hasta que se elija una nueva rama LTS, momento en el cual la serie v1.6.x ya no recibirá correcciones de errores regulares y se aconsejará a todos menos a los usuarios más conservadores que actualicen a la nueva serie de versiones LTS. Como desarrollador de paquetes, puede que prefieras desarrollar para la versión LTS, para maximizar el número de usuarios que pueden usar tu paquete. Según SemVer, el código escrito para v1.0 seguirá funcionando para todas las futuras versiones LTS y Estables. En general, incluso si se apunta a la LTS, se puede desarrollar y ejecutar código en la última versión Estable, para aprovechar el rendimiento mejorado; siempre que se evite usar nuevas características (como funciones de biblioteca añadidas o nuevos métodos).

Es posible que prefieras la versión nocturna de Julia si deseas aprovechar las últimas actualizaciones del lenguaje y no te importa si la versión disponible hoy ocasionalmente no funciona. Como su nombre indica, las versiones de la versión nocturna se realizan aproximadamente cada noche (dependiendo de la estabilidad de la infraestructura de construcción). En general, las versiones nocturnas son bastante seguras de usar: tu código no se incendiará. Sin embargo, pueden haber regresiones ocasionales y/o problemas que no se encontrarán hasta que se realicen pruebas más exhaustivas antes del lanzamiento. Es posible que desees probar contra la versión nocturna para asegurarte de que tales regresiones que afectan tu caso de uso se detecten antes de que se realice un lanzamiento.

Finalmente, también puedes considerar compilar Julia desde el código fuente por ti mismo. Esta opción es principalmente para aquellas personas que se sienten cómodas en la línea de comandos o que están interesadas en aprender. Si esto te describe, también puede que te interese leer nuestro [guidelines for contributing](https://github.com/JuliaLang/julia/blob/master/CONTRIBUTING.md).

Los enlaces a cada uno de estos tipos de descarga se pueden encontrar en la página de descarga en [https://julialang.org/downloads/](https://julialang.org/downloads/). Tenga en cuenta que no todas las versiones de Julia están disponibles para todas las plataformas.

### How can I transfer the list of installed packages after updating my version of Julia?

Cada versión menor de Julia tiene su propio [environment](https://docs.julialang.org/en/v1/manual/code-loading/#Environments-1) por defecto. Como resultado, al instalar una nueva versión menor de Julia, los paquetes que agregaste usando la versión menor anterior no estarán disponibles por defecto. El entorno para una versión dada de Julia está definido por los archivos `Project.toml` y `Manifest.toml` en una carpeta que coincide con el número de versión en `.julia/environments/`, por ejemplo, `.julia/environments/v1.3`.

Si instalas una nueva versión menor de Julia, digamos `1.4`, y quieres usar en su entorno predeterminado los mismos paquetes que en una versión anterior (por ejemplo, `1.3`), puedes copiar el contenido del archivo `Project.toml` de la carpeta `1.3` a `1.4`. Luego, en una sesión de la nueva versión de Julia, ingresa al "modo de gestión de paquetes" presionando la tecla `]`, y ejecuta el comando [`instantiate`](https://julialang.github.io/Pkg.jl/v1/api/#Pkg.instantiate).

Esta operación resolverá un conjunto de paquetes viables del archivo copiado que son compatibles con la versión objetivo de Julia, y los instalará o actualizará si es adecuado. Si deseas reproducir no solo el conjunto de paquetes, sino también las versiones que estabas utilizando en la versión anterior de Julia, también deberías copiar el archivo `Manifest.toml` antes de ejecutar el comando Pkg `instantiate`. Sin embargo, ten en cuenta que los paquetes pueden definir restricciones de compatibilidad que pueden verse afectadas al cambiar la versión de Julia, por lo que el conjunto exacto de versiones que tenías en `1.3` puede no funcionar para `1.4`.
