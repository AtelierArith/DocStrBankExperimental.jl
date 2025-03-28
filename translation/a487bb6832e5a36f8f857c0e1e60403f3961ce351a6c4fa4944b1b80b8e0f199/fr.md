```
TestLogger(; min_level=Info, catch_exceptions=false)
```

Créez un `TestLogger` qui capture les messages enregistrés dans son champ `logs::Vector{LogRecord}`.

Définissez `min_level` pour contrôler le `LogLevel`, `catch_exceptions` pour déterminer si les exceptions levées lors de la génération d'événements de journalisation doivent être capturées, et `respect_maxlog` pour savoir s'il faut suivre la convention de journaliser des messages avec `maxlog=n` pour un certain entier `n` au maximum `n` fois.

Voir aussi : [`LogRecord`](@ref).

## Exemples

```jldoctest
julia> using Test, Logging

julia> f() = @info "Hi" number=5;

julia> test_logger = TestLogger();

julia> with_logger(test_logger) do
           f()
           @info "Bye!"
       end

julia> @test test_logger.logs[1].message == "Hi"
Test Passed

julia> @test test_logger.logs[1].kwargs[:number] == 5
Test Passed

julia> @test test_logger.logs[2].message == "Bye!"
Test Passed
```
