```
@test_skip ex
@test_skip f(args...) key=val ...
```

Marca una prueba que no debe ejecutarse pero que debe incluirse en el informe de resumen de pruebas como `Rota`. Esto puede ser útil para pruebas que fallan intermitentemente, o pruebas de funcionalidades que aún no se han implementado. Esto es equivalente a [`@test ex skip=true`](@ref @test).

La forma `@test_skip f(args...) key=val...` funciona como para el macro `@test`.

# Ejemplos

```jldoctest
julia> @test_skip 1 == 2
Prueba Rota
  Omitida: 1 == 2

julia> @test_skip 1 == 2 atol=0.1
Prueba Rota
  Omitida: ==(1, 2, atol = 0.1)
```
