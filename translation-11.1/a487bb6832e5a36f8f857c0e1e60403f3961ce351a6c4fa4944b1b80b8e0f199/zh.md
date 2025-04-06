```
TestLogger(; min_level=Info, catch_exceptions=false)
```

创建一个 `TestLogger`，它在其 `logs::Vector{LogRecord}` 字段中捕获记录的消息。

设置 `min_level` 来控制 `LogLevel`，`catch_exceptions` 用于决定是否捕获作为日志事件生成一部分抛出的异常，以及 `respect_maxlog` 用于决定是否遵循使用 `maxlog=n` 记录消息的约定，其中某个整数 `n` 最多记录 `n` 次。

另请参见: [`LogRecord`](@ref)。

## 示例

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
