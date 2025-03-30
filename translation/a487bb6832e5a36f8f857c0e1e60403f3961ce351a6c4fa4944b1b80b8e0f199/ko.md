```
TestLogger(; min_level=Info, catch_exceptions=false)
```

`logs::Vector{LogRecord}` 필드에 기록된 메시지를 캡처하는 `TestLogger`를 생성합니다.

`min_level`을 설정하여 `LogLevel`을 제어하고, `catch_exceptions`는 로그 이벤트 생성의 일환으로 발생하는 예외를 포착할지 여부를 설정하며, `respect_maxlog`는 `maxlog=n`으로 메시지를 기록하는 관습을 따를지 여부를 설정합니다. 여기서 `n`은 최대 `n`회까지의 정수입니다.

자세한 내용은 [`LogRecord`](@ref)를 참조하세요.

## 예제

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
