```
TestLogger(; min_level=Info, catch_exceptions=false)
```

Erstellen Sie einen `TestLogger`, der protokollierte Nachrichten in seinem Feld `logs::Vector{LogRecord}` erfasst.

Setzen Sie `min_level`, um das `LogLevel` zu steuern, `catch_exceptions`, um festzulegen, ob Ausnahmen, die im Rahmen der Protokollereigniserzeugung ausgelöst werden, erfasst werden sollen, und `respect_maxlog`, um festzulegen, ob die Konvention befolgt werden soll, Nachrichten mit `maxlog=n` für eine ganze Zahl `n` höchstens `n` Mal zu protokollieren.

Siehe auch: [`LogRecord`](@ref).

## Beispiele

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
