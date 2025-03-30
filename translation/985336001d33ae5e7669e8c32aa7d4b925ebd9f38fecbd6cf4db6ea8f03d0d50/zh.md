```
with_logger(function, logger)
```

执行 `function`，将所有日志消息定向到 `logger`。

# 示例

```julia
function test(x)
    @info "x = $x"
end

with_logger(logger) do
    test(1)
    test([1,2])
end
```
