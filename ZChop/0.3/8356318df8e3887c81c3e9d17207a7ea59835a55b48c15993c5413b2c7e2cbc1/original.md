```
nchop(x, args...; digits=14, kwargs...)
```

Round `x` if it is a number, or elements in `x` if it is a, possibly nested, container. `args` and `kwargs` are passed to `round`. `nchop` does not modify the input `x`.

Passing a type, for example `Int` as the first argument to `round` is not supported.

See also `zchop`, `zchop!`, and `nchop!`.
