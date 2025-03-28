```
with_logger(function, logger)
```

Exécutez `function`, en dirigeant tous les messages de journal vers `logger`.

# Exemples

```julia
function test(x)
    @info "x = $x"
end

with_logger(logger) do
    test(1)
    test([1,2])
end
```
