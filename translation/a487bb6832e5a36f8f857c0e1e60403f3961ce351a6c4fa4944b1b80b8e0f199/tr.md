```
TestLogger(; min_level=Info, catch_exceptions=false)
```

`logs::Vector{LogRecord}` alanında kaydedilen mesajları yakalayan bir `TestLogger` oluşturun.

`LogLevel`'ı kontrol etmek için `min_level`'i, log olayı oluşturma sırasında atılan istisnaların yakalanıp yakalanmayacağını belirlemek için `catch_exceptions`'ı ve en fazla `n` kez loglama konvansiyonunu takip edip etmeyeceğini belirlemek için `respect_maxlog`'ı ayarlayın.

Ayrıca bkz: [`LogRecord`](@ref).

## Örnekler

```jldoctest
julia> using Test, Logging

julia> f() = @info "Merhaba" number=5;

julia> test_logger = TestLogger();

julia> with_logger(test_logger) do
           f()
           @info "Hoşça kal!"
       end

julia> @test test_logger.logs[1].message == "Merhaba"
Test Passed

julia> @test test_logger.logs[1].kwargs[:number] == 5
Test Passed

julia> @test test_logger.logs[2].message == "Hoşça kal!"
Test Passed
```
