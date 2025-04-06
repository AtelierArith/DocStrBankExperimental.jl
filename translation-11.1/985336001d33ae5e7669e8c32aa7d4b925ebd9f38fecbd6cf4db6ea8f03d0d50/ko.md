```
with_logger(function, logger)
```

`function`을 실행하고 모든 로그 메시지를 `logger`로 전달합니다.

# 예시

```julia
function test(x)
    @info "x = $x"
end

with_logger(logger) do
    test(1)
    test([1,2])
end
```
