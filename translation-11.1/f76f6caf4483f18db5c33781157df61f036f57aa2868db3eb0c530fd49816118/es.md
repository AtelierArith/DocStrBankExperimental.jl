```
@testset [CustomTestSet] [options...] ["descripción"] begin test_ex end
@testset [CustomTestSet] [options...] ["descripción $v"] for v in itr test_ex end
@testset [CustomTestSet] [options...] ["descripción $v, $w"] for v in itrv, w in itrw test_ex end
@testset [CustomTestSet] [options...] ["descripción"] test_func()
@testset let v = v, w = w; test_ex; end
```

# Con begin/end o llamada a función

Cuando se utiliza @testset, con begin/end o una sola llamada a función, la macro inicia un nuevo conjunto de pruebas en el que evaluar la expresión dada.

Si no se proporciona un tipo de conjunto de pruebas personalizado, se crea por defecto un `DefaultTestSet`. `DefaultTestSet` registra todos los resultados y, si hay algún `Fail` o `Error`, lanza una excepción al final del conjunto de pruebas de nivel superior (no anidado), junto con un resumen de los resultados de las pruebas.

Se puede proporcionar cualquier tipo de conjunto de pruebas personalizado (subtipo de `AbstractTestSet`) y también se utilizará para cualquier invocación anidada de `@testset`. Las opciones dadas solo se aplican al conjunto de pruebas donde se proporcionan. El tipo de conjunto de pruebas por defecto acepta tres opciones booleanas:

  * `verbose`: si es `true`, se muestra el resumen de resultados de los conjuntos de pruebas anidados incluso cuando todos pasan (el valor por defecto es `false`).
  * `showtiming`: si es `true`, se muestra la duración de cada conjunto de pruebas mostrado (el valor por defecto es `true`).
  * `failfast`: si es `true`, cualquier fallo de prueba o error hará que el conjunto de pruebas y cualquier conjunto de pruebas hijo devuelvan inmediatamente (el valor por defecto es `false`). Esto también se puede establecer globalmente a través de la variable de entorno `JULIA_TEST_FAILFAST`.

!!! compat "Julia 1.8"
    `@testset test_func()` requiere al menos Julia 1.8.


!!! compat "Julia 1.9"
    `failfast` requiere al menos Julia 1.9.


La cadena de descripción acepta interpolación de los índices del bucle. Si no se proporciona una descripción, se construye una basada en las variables. Si se proporciona una llamada a función, se utilizará su nombre. Las cadenas de descripción explícitas anulan este comportamiento.

Por defecto, la macro `@testset` devolverá el objeto del conjunto de pruebas en sí, aunque este comportamiento se puede personalizar en otros tipos de conjuntos de pruebas. Si se utiliza un bucle `for`, entonces la macro recopila y devuelve una lista de los valores de retorno del método `finish`, que por defecto devolverá una lista de los objetos de conjunto de pruebas utilizados en cada iteración.

Antes de la ejecución del cuerpo de un `@testset`, hay una llamada implícita a `Random.seed!(seed)` donde `seed` es la semilla actual del generador de números aleatorios global. Además, después de la ejecución del cuerpo, el estado del generador de números aleatorios global se restaura a lo que era antes del `@testset`. Esto está destinado a facilitar la reproducibilidad en caso de fallo y permitir reordenamientos sin problemas de los `@testset` independientemente de su efecto secundario en el estado del generador de números aleatorios global.

## Ejemplos

```jldoctest; filter = r"identidades trigonométricas |    4      4  [0-9\.]+s"
julia> @testset "identidades trigonométricas" begin
           θ = 2/3*π
           @test sin(-θ) ≈ -sin(θ)
           @test cos(-θ) ≈ cos(θ)
           @test sin(2θ) ≈ 2*sin(θ)*cos(θ)
           @test cos(2θ) ≈ cos(θ)^2 - sin(θ)^2
       end;
Resumen de Pruebas:      | Pasar  Total  Tiempo
identidades trigonométricas |    4      4  0.2s
```

# `@testset for`

Cuando se utiliza `@testset for`, la macro inicia una nueva prueba para cada iteración del bucle proporcionado. La semántica de cada conjunto de pruebas es de otro modo idéntica a la del caso `begin/end` (como si se usara para cada iteración del bucle).

# `@testset let`

Cuando se utiliza `@testset let`, la macro inicia un conjunto de pruebas *transparente* con el objeto dado añadido como un objeto de contexto a cualquier prueba fallida contenida en él. Esto es útil al realizar un conjunto de pruebas relacionadas sobre un objeto más grande y es deseable imprimir este objeto más grande cuando alguna de las pruebas individuales falla. Los conjuntos de pruebas transparentes no introducen niveles adicionales de anidamiento en la jerarquía del conjunto de pruebas y se pasan directamente al conjunto de pruebas padre (con el objeto de contexto añadido a cualquier prueba fallida).

!!! compat "Julia 1.9"
    `@testset let` requiere al menos Julia 1.9.


!!! compat "Julia 1.10"
    Se admiten múltiples asignaciones `let` desde Julia 1.10.


## Ejemplos

```jldoctest
julia> @testset let logi = log(im)
           @test imag(logi) == π/2
           @test !iszero(real(logi))
       end
Prueba Fallida en none:3
  Expresión: !(iszero(real(logi)))
     Contexto: logi = 0.0 + 1.5707963267948966im

ERROR: Hubo un error durante la prueba

julia> @testset let logi = log(im), op = !iszero
           @test imag(logi) == π/2
           @test op(real(logi))
       end
Prueba Fallida en none:3
  Expresión: op(real(logi))
     Contexto: logi = 0.0 + 1.5707963267948966im
              op = !iszero

ERROR: Hubo un error durante la prueba
```
