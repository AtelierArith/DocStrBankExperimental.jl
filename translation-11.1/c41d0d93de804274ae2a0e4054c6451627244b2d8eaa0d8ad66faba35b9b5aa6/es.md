```
@test ex
@test f(args...) key=val ...
@test ex broken=true
@test ex skip=true
```

Prueba que la expresión `ex` evalúe a `true`. Si se ejecuta dentro de un `@testset`, devuelve un `Pass` `Result` si lo hace, un `Fail` `Result` si es `false`, y un `Error` `Result` si no se pudo evaluar. Si se ejecuta fuera de un `@testset`, lanza una excepción en lugar de devolver `Fail` o `Error`.

# Ejemplos

```jldoctest
julia> @test true
Test Passed

julia> @test [1, 2] + [2, 1] == [3, 3]
Test Passed
```

La forma `@test f(args...) key=val...` es equivalente a escribir `@test f(args..., key=val...)`, lo cual puede ser útil cuando la expresión es una llamada que utiliza sintaxis infija, como comparaciones aproximadas:

```jldoctest
julia> @test π ≈ 3.14 atol=0.01
Test Passed
```

Esto es equivalente a la prueba más fea `@test ≈(π, 3.14, atol=0.01)`. Es un error proporcionar más de una expresión a menos que la primera sea una expresión de llamada y el resto sean asignaciones (`k=v`).

Puedes usar cualquier clave para los argumentos `key=val`, excepto para `broken` y `skip`, que tienen significados especiales en el contexto de `@test`:

  * `broken=cond` indica una prueba que debería pasar pero que actualmente falla consistentemente cuando `cond==true`. Pruebas que la expresión `ex` evalúe a `false` o cause una excepción. Devuelve un `Broken` `Result` si lo hace, o un `Error` `Result` si la expresión evalúa a `true`. La prueba regular `@test ex` se evalúa cuando `cond==false`.
  * `skip=cond` marca una prueba que no debería ejecutarse pero que debería incluirse en el informe de resumen de pruebas como `Broken`, cuando `cond==true`. Esto puede ser útil para pruebas que fallan intermitentemente, o pruebas de funcionalidades que aún no se han implementado. La prueba regular `@test ex` se evalúa cuando `cond==false`.

# Ejemplos

```jldoctest
julia> @test 2 + 2 ≈ 6 atol=1 broken=true
Test Broken
  Expression: ≈(2 + 2, 6, atol = 1)

julia> @test 2 + 2 ≈ 5 atol=1 broken=false
Test Passed

julia> @test 2 + 2 == 5 skip=true
Test Broken
  Skipped: 2 + 2 == 5

julia> @test 2 + 2 == 4 skip=false
Test Passed
```

!!! compat "Julia 1.7"
    Los argumentos de palabra clave `broken` y `skip` requieren al menos Julia 1.7.

