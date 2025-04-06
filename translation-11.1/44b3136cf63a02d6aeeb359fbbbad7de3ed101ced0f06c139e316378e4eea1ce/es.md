```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Test/docs/src/index.md"
```

# Unit Testing

```@meta
DocTestSetup = :(using Test)
```

## Testing Base Julia

Julia está en un desarrollo rápido y tiene un extenso conjunto de pruebas para verificar la funcionalidad en múltiples plataformas. Si construyes Julia desde el código fuente, puedes ejecutar este conjunto de pruebas con `make test`. En una instalación binaria, puedes ejecutar el conjunto de pruebas usando `Base.runtests()`.

```@docs
Base.runtests
```

## Basic Unit Tests

El módulo `Test` proporciona una funcionalidad simple de *pruebas unitarias*. Las pruebas unitarias son una forma de ver si tu código es correcto al verificar que los resultados son los que esperas. Puede ser útil para asegurarte de que tu código siga funcionando después de realizar cambios, y se puede utilizar durante el desarrollo como una forma de especificar los comportamientos que tu código debería tener cuando esté completo. También puede que desees consultar la documentación de [adding tests to your Julia Package](https://pkgdocs.julialang.org/dev/creating-packages/#Adding-tests-to-the-package).

Las pruebas unitarias simples se pueden realizar con los macros `@test` y `@test_throws`:

```@docs
Test.@test
Test.@test_throws
```

Por ejemplo, supongamos que queremos verificar que nuestra nueva función `foo(x)` funciona como se espera:

```jldoctest testfoo
julia> using Test

julia> foo(x) = length(x)^2
foo (generic function with 1 method)
```

Si la condición es verdadera, se devuelve un `Pass`:

```jldoctest testfoo
julia> @test foo("bar") == 9
Test Passed

julia> @test foo("fizz") >= 10
Test Passed
```

Si la condición es falsa, entonces se devuelve un `Fail` y se lanza una excepción:

```jldoctest testfoo
julia> @test foo("f") == 20
Test Failed at none:1
  Expression: foo("f") == 20
   Evaluated: 1 == 20

ERROR: There was an error during testing
```

Si la condición no se pudo evaluar porque se lanzó una excepción, lo que ocurre en este caso porque `length` no está definido para símbolos, se devuelve un objeto `Error` y se lanza una excepción:

```julia-repl
julia> @test foo(:cat) == 1
Error During Test
  Test threw an exception of type MethodError
  Expression: foo(:cat) == 1
  MethodError: no method matching length(::Symbol)
  The function `length` exists, but no method is defined for this combination of argument types.

  Closest candidates are:
    length(::SimpleVector) at essentials.jl:256
    length(::Base.MethodList) at reflection.jl:521
    length(::MethodTable) at reflection.jl:597
    ...
  Stacktrace:
  [...]
ERROR: There was an error during testing
```

Si esperamos que evaluar una expresión *debería* lanzar una excepción, entonces podemos usar `@test_throws` para verificar que esto ocurra:

```jldoctest testfoo
julia> @test_throws MethodError foo(:cat)
Test Passed
      Thrown: MethodError
```

## Working with Test Sets

Típicamente, se utiliza un gran número de pruebas para asegurarse de que las funciones funcionen correctamente en una variedad de entradas. En caso de que una prueba falle, el comportamiento predeterminado es lanzar una excepción de inmediato. Sin embargo, normalmente es preferible ejecutar el resto de las pruebas primero para obtener una mejor idea de cuántos errores hay en el código que se está probando.

!!! note
    El `@testset` creará un ámbito local propio al ejecutar las pruebas en él.


El macro `@testset` se puede utilizar para agrupar pruebas en *conjuntos*. Todas las pruebas en un conjunto de pruebas se ejecutarán, y al final del conjunto de pruebas se imprimirá un resumen. Si alguna de las pruebas falla, o no se puede evaluar debido a un error, el conjunto de pruebas lanzará una `TestSetException`.

```@docs
Test.@testset
Test.TestSetException
```

Podemos poner nuestras pruebas para la función `foo(x)` en un conjunto de pruebas:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @test foo("a")   == 1
           @test foo("ab")  == 4
           @test foo("abc") == 9
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    3      3  0.0s
```

Los conjuntos de prueba también pueden estar anidados:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @testset "Animals" begin
               @test foo("cat") == 9
               @test foo("dog") == foo("cat")
           end
           @testset "Arrays $i" for i in 1:3
               @test foo(zeros(i)) == i^2
               @test foo(fill(1.0, i)) == i^2
           end
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    8      8  0.0s
```

Así como llamar funciones:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> f(x) = @test isone(x)
f (generic function with 1 method)

julia> @testset f(1);
Test Summary: | Pass  Total  Time
f             |    1      1  0.0s
```

Esto se puede usar para permitir la factorización de conjuntos de pruebas, facilitando la ejecución de conjuntos de pruebas individuales al ejecutar en su lugar las funciones asociadas. Tenga en cuenta que en el caso de funciones, al conjunto de pruebas se le dará el nombre de la función llamada. En el caso de que un conjunto de pruebas anidado no tenga fallos, como ocurrió aquí, se ocultará en el resumen, a menos que se pase la opción `verbose=true`:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset verbose = true "Foo Tests" begin
           @testset "Animals" begin
               @test foo("cat") == 9
               @test foo("dog") == foo("cat")
           end
           @testset "Arrays $i" for i in 1:3
               @test foo(zeros(i)) == i^2
               @test foo(fill(1.0, i)) == i^2
           end
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    8      8  0.0s
  Animals     |    2      2  0.0s
  Arrays 1    |    2      2  0.0s
  Arrays 2    |    2      2  0.0s
  Arrays 3    |    2      2  0.0s
```

Si tenemos un fallo en la prueba, solo se mostrarán los detalles de los conjuntos de pruebas fallidos:

```julia-repl; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @testset "Animals" begin
               @testset "Felines" begin
                   @test foo("cat") == 9
               end
               @testset "Canines" begin
                   @test foo("dog") == 9
               end
           end
           @testset "Arrays" begin
               @test foo(zeros(2)) == 4
               @test foo(fill(1.0, 4)) == 15
           end
       end

Arrays: Test Failed
  Expression: foo(fill(1.0, 4)) == 15
   Evaluated: 16 == 15
[...]
Test Summary: | Pass  Fail  Total  Time
Foo Tests     |    3     1      4  0.0s
  Animals     |    2            2  0.0s
  Arrays      |    1     1      2  0.0s
ERROR: Some tests did not pass: 3 passed, 1 failed, 0 errored, 0 broken.
```

## Testing Log Statements

Uno puede usar el [`@test_logs`](@ref) macro para probar declaraciones de registro, o usar un [`TestLogger`](@ref).

```@docs
Test.@test_logs
Test.TestLogger
Test.LogRecord
```

## Other Test Macros

Dado que los cálculos con valores de punto flotante pueden ser imprecisos, puedes realizar verificaciones de igualdad aproximada utilizando `@test a ≈ b` (donde `≈`, escrito a través de la autocompletación de `\approx`, es la función [`isapprox`](@ref)) o usar `4d61726b646f776e2e436f64652822222c20226973617070726f782229_40726566` directamente.

```jldoctest
julia> @test 1 ≈ 0.999999999
Test Passed

julia> @test 1 ≈ 0.999999
Test Failed at none:1
  Expression: 1 ≈ 0.999999
   Evaluated: 1 ≈ 0.999999

ERROR: There was an error during testing
```

Puedes especificar tolerancias relativas y absolutas configurando los argumentos de palabra clave `rtol` y `atol` de `isapprox`, respectivamente, después de la comparación `≈`:

```jldoctest
julia> @test 1 ≈ 0.999999  rtol=1e-5
Test Passed
```

Tenga en cuenta que esta no es una característica específica del `≈`, sino más bien una característica general de la macro `@test`: `@test a <op> b key=val` es transformado por la macro en `@test op(a, b, key=val)`. Sin embargo, es particularmente útil para pruebas `≈`.

```@docs
Test.@inferred
Test.@test_deprecated
Test.@test_warn
Test.@test_nowarn
```

## Broken Tests

Si una prueba falla de manera consistente, se puede cambiar para usar el macro `@test_broken`. Esto denotará la prueba como `Rota` si la prueba sigue fallando y alertará al usuario a través de un `Error` si la prueba tiene éxito.

```@docs
Test.@test_broken
```

`@test_skip` también está disponible para omitir una prueba sin evaluación, pero contando la prueba omitida en el informe del conjunto de pruebas. La prueba no se ejecutará pero dará un `Resultado` `Roto`.

```@docs
Test.@test_skip
```

## Test result types

```@docs
Test.Result
Test.Pass
Test.Fail
Test.Error
Test.Broken
```

## Creating Custom `AbstractTestSet` Types

Los paquetes pueden crear sus propios subtipos de `AbstractTestSet` implementando los métodos `record` y `finish`. El subtipo debe tener un constructor de un argumento que tome una cadena de descripción, con cualquier opción pasada como argumentos de palabra clave.

```@docs
Test.record
Test.finish
```

`Test` asume la responsabilidad de mantener una pila de conjuntos de pruebas anidados a medida que se ejecutan, pero cualquier acumulación de resultados es responsabilidad del subtipo `AbstractTestSet`. Puedes acceder a esta pila con los métodos `get_testset` y `get_testset_depth`. Ten en cuenta que estas funciones no están exportadas.

```@docs
Test.get_testset
Test.get_testset_depth
```

`Test` también se asegura de que las invocaciones anidadas de `@testset` utilicen el mismo subtipo de `AbstractTestSet` que su padre, a menos que se establezca explícitamente. No propaga ninguna propiedad del testset. El comportamiento de herencia de opciones se puede implementar mediante paquetes utilizando la infraestructura de pila que proporciona `Test`.

Definir un subtipo básico de `AbstractTestSet` podría verse así:

```julia
import Test: Test, record, finish
using Test: AbstractTestSet, Result, Pass, Fail, Error
using Test: get_testset_depth, get_testset
struct CustomTestSet <: Test.AbstractTestSet
    description::AbstractString
    foo::Int
    results::Vector
    # constructor takes a description string and options keyword arguments
    CustomTestSet(desc; foo=1) = new(desc, foo, [])
end

record(ts::CustomTestSet, child::AbstractTestSet) = push!(ts.results, child)
record(ts::CustomTestSet, res::Result) = push!(ts.results, res)
function finish(ts::CustomTestSet)
    # just record if we're not the top-level parent
    if get_testset_depth() > 0
        record(get_testset(), ts)
        return ts
    end

    # so the results are printed if we are at the top level
    Test.print_test_results(ts)
    return ts
end
```

Y usando ese conjunto de pruebas se ve así:

```julia
@testset CustomTestSet foo=4 "custom testset inner 2" begin
    # this testset should inherit the type, but not the argument.
    @testset "custom testset inner" begin
        @test true
    end
end
```

Para utilizar un conjunto de pruebas personalizado y tener los resultados grabados impresos como parte de cualquier conjunto de pruebas predeterminado externo, también define `Test.get_test_counts`. Esto podría verse así:

```julia
using Test: AbstractTestSet, Pass, Fail, Error, Broken, get_test_counts, TestCounts, format_duration

function Test.get_test_counts(ts::CustomTestSet)
    passes, fails, errors, broken = 0, 0, 0, 0
    # cumulative results
    c_passes, c_fails, c_errors, c_broken = 0, 0, 0, 0

    for t in ts.results
        # count up results
        isa(t, Pass)   && (passes += 1)
        isa(t, Fail)   && (fails  += 1)
        isa(t, Error)  && (errors += 1)
        isa(t, Broken) && (broken += 1)
        # handle children
        if isa(t, AbstractTestSet)
            tc = get_test_counts(t)::TestCounts
            c_passes += tc.passes + tc.cumulative_passes
            c_fails  += tc.fails + tc.cumulative_fails
            c_errors += tc.errors + tc.cumulative_errors
            c_broken += tc.broken + tc.cumulative_broken
        end
    end
    # get a duration, if we have one
    duration = format_duration(ts)
    return TestCounts(true, passes, fails, errors, broken, c_passes, c_fails, c_errors, c_broken, duration)
end
```

```@docs
Test.TestCounts
Test.get_test_counts
Test.format_duration
Test.print_test_results
```

## Test utilities

```@docs
Test.GenericArray
Test.GenericDict
Test.GenericOrder
Test.GenericSet
Test.GenericString
Test.detect_ambiguities
Test.detect_unbound_args
```

## Workflow for Testing Packages

Usando las herramientas disponibles en las secciones anteriores, aquí hay un flujo de trabajo potencial para crear un paquete y agregarle pruebas.

### Generating an Example Package

Para este flujo de trabajo, crearemos un paquete llamado `Example`:

```julia
pkg> generate Example
shell> cd Example
shell> mkdir test
pkg> activate .
```

### Creating Sample Functions

El requisito número uno para probar un paquete es tener funcionalidad para probar. Para eso, agregaremos algunas funciones simples a `Example` que podamos probar. Agrega lo siguiente a `src/Example.jl`:

```julia
module Example

function greet()
    "Hello world!"
end

function simple_add(a, b)
    a + b
end

function type_multiply(a::Float64, b::Float64)
    a * b
end

export greet, simple_add, type_multiply

end
```

### Creating a Test Environment

Desde la raíz del paquete `Example`, navega al directorio `test`, activa un nuevo entorno allí y añade el paquete `Test` al entorno:

```julia
shell> cd test
pkg> activate .
(test) pkg> add Test
```

### Testing Our Package

Ahora, estamos listos para agregar pruebas a `Example`. Es una práctica estándar crear un archivo dentro del directorio `test` llamado `runtests.jl` que contenga los conjuntos de pruebas que queremos ejecutar. Adelante, crea ese archivo dentro del directorio `test` y agrega el siguiente código:

```julia
using Example
using Test

@testset "Example tests" begin

    @testset "Math tests" begin
        include("math_tests.jl")
    end

    @testset "Greeting tests" begin
        include("greeting_tests.jl")
    end
end
```

Necesitaremos crear esos dos archivos incluidos, `math_tests.jl` y `greeting_tests.jl`, y agregar algunas pruebas a ellos.

> **Nota:** Observa cómo no tuvimos que especificar agregar `Example` en el `Project.toml` del entorno `test`. Este es un beneficio del sistema de pruebas de Julia que podrías [read about more here](https://pkgdocs.julialang.org/dev/creating-packages/).


#### Writing Tests for `math_tests.jl`

Usando nuestro conocimiento de `Test.jl`, aquí hay algunas pruebas de ejemplo que podríamos agregar a `math_tests.jl`:

```julia
@testset "Testset 1" begin
    @test 2 == simple_add(1, 1)
    @test 3.5 == simple_add(1, 2.5)
        @test_throws MethodError simple_add(1, "A")
        @test_throws MethodError simple_add(1, 2, 3)
end

@testset "Testset 2" begin
    @test 1.0 == type_multiply(1.0, 1.0)
        @test isa(type_multiply(2.0, 2.0), Float64)
    @test_throws MethodError type_multiply(1, 2.5)
end
```

#### Writing Tests for `greeting_tests.jl`

Usando nuestro conocimiento de `Test.jl`, aquí hay algunos ejemplos de pruebas que podríamos agregar a `greeting_tests.jl`:

```julia
@testset "Testset 3" begin
    @test "Hello world!" == greet()
    @test_throws MethodError greet("Antonia")
end
```

### Testing Our Package

Ahora que hemos agregado nuestras pruebas y nuestro script `runtests.jl` en `test`, podemos probar nuestro paquete `Example` volviendo a la raíz del entorno del paquete `Example` y reactivando el entorno `Example`:

```julia
shell> cd ..
pkg> activate .
```

A partir de ahí, finalmente podemos ejecutar nuestra suite de pruebas de la siguiente manera:

```julia
(Example) pkg> test
     Testing Example
      Status `/tmp/jl_Yngpvy/Project.toml`
  [fa318bd2] Example v0.1.0 `/home/src/Projects/tmp/errata/Example`
  [8dfed614] Test `@stdlib/Test`
      Status `/tmp/jl_Yngpvy/Manifest.toml`
  [fa318bd2] Example v0.1.0 `/home/src/Projects/tmp/errata/Example`
  [2a0f44e3] Base64 `@stdlib/Base64`
  [b77e0a4c] InteractiveUtils `@stdlib/InteractiveUtils`
  [56ddb016] Logging `@stdlib/Logging`
  [d6f4376e] Markdown `@stdlib/Markdown`
  [9a3f8284] Random `@stdlib/Random`
  [ea8e919c] SHA `@stdlib/SHA`
  [9e88b42a] Serialization `@stdlib/Serialization`
  [8dfed614] Test `@stdlib/Test`
     Testing Running tests...
Test Summary: | Pass  Total
Example tests |    9      9
     Testing Example tests passed
```

Y si todo salió correctamente, deberías ver una salida similar a la anterior. Usando `Test.jl`, se pueden agregar pruebas más complicadas para los paquetes, pero esto debería, idealmente, orientar a los desarrolladores en la dirección de cómo comenzar a probar sus propios paquetes creados.

```@meta
DocTestSetup = nothing
```

### Code Coverage

El seguimiento de la cobertura de código durante las pruebas se puede habilitar utilizando la bandera `pkg> test --coverage` (o a un nivel más bajo utilizando el argumento de julia [`--code-coverage`](@ref command-line-interface)). Esto está activado por defecto en la acción de GitHub [julia-runtest](https://github.com/julia-actions/julia-runtest).

To evaluate coverage either manually inspect the `.cov` files that are generated beside the source files locally, or in CI use the [julia-processcoverage](https://github.com/julia-actions/julia-processcoverage) GitHub action.

!!! compat "Julia 1.11"
    Desde Julia 1.11, la cobertura no se recopila durante la fase de precompilación del paquete.

