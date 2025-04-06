```
with_logger(function, logger)
```

`function`'ı çalıştırın, tüm günlük mesajlarını `logger`'a yönlendirin.

# Örnekler

```julia
function test(x)
    @info "x = $x"
end

with_logger(logger) do
    test(1)
    test([1,2])
end
```
