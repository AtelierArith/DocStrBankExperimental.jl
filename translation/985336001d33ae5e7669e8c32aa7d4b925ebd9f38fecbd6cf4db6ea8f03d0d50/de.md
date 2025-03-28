```
with_logger(function, logger)
```

Führen Sie `function` aus und leiten Sie alle Protokollnachrichten an `logger` weiter.

# Beispiele

```julia
function test(x)
    @info "x = $x"
end

with_logger(logger) do
    test(1)
    test([1,2])
end
```
