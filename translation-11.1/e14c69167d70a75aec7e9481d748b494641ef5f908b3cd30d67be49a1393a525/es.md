```
dlopen_e(libfile::AbstractString [, flags::Integer])
```

Similar a [`dlopen`](@ref), excepto que devuelve `C_NULL` en lugar de generar errores. Este método ahora está en desuso a favor de `dlopen(libfile::AbstractString [, flags::Integer]; throw_error=false)`.
