```
@test_broken ex
@test_broken f(args...) key=val ...
```

Indica una prueba que debería pasar pero que actualmente falla de manera consistente. Prueba que la expresión `ex` evalúa a `false` o causa una excepción. Devuelve un `Result` `Broken` si lo hace, o un `Result` `Error` si la expresión evalúa a `true`. Esto es equivalente a [`@test ex broken=true`](@ref @test).

La forma `@test_broken f(args...) key=val...` funciona como para la macro `@test`.

# Ejemplos

```jldoctest
julia> @test_broken 1 == 2
Prueba Rota
  Expresión: 1 == 2

julia> @test_broken 1 == 2 atol=0.1
Prueba Rota
  Expresión: ==(1, 2, atol = 0.1)
```
