```
TestLogger(; min_level=Info, catch_exceptions=false)
```

Crea un `TestLogger` que captura los mensajes registrados en su campo `logs::Vector{LogRecord}`.

Establece `min_level` para controlar el `LogLevel`, `catch_exceptions` para determinar si las excepciones lanzadas como parte de la generación de eventos de registro deben ser capturadas, y `respect_maxlog` para decidir si se debe seguir la convención de registrar mensajes con `maxlog=n` para algún entero `n` un máximo de `n` veces.

Ver también: [`LogRecord`](@ref).

## Ejemplos

```jldoctest
julia> using Test, Logging

julia> f() = @info "Hola" number=5;

julia> test_logger = TestLogger();

julia> with_logger(test_logger) do
           f()
           @info "¡Adiós!"
       end

julia> @test test_logger.logs[1].message == "Hola"
Test Passed

julia> @test test_logger.logs[1].kwargs[:number] == 5
Test Passed

julia> @test test_logger.logs[2].message == "¡Adiós!"
Test Passed
```
