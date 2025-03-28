```
TestLogger(; min_level=Info, catch_exceptions=false)
```

`logs::Vector{LogRecord}` フィールドにログメッセージをキャプチャする `TestLogger` を作成します。

`min_level` を設定して `LogLevel` を制御し、`catch_exceptions` を使用してログイベント生成の一部としてスローされた例外をキャッチするかどうかを指定し、`respect_maxlog` を使用して、整数 `n` に対して `maxlog=n` でメッセージを最大 `n` 回までログするという慣習に従うかどうかを指定します。

詳細については、[`LogRecord`](@ref) を参照してください。

## 例

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
