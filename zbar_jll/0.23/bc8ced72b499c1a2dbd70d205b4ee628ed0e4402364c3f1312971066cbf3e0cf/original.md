```
zbarimg(f::Function; adjust_PATH::Bool=true, adjust_LIBPATH::Bool=true)
```

An `ExecutableProduct` wrapper that supports the execution of zbarimg.

!!! warning "Deprecated"
    This method is deprecated because it is not thread-safe and will be removed in future Julia versions. Use the non do-block form instead.


# Example

```julia
zbarimg() do exe
    run(`$exe $arguments`)
end
```

!!! compat "Julia 1.3"
    This method requires Julia version 1.3 or newer.

