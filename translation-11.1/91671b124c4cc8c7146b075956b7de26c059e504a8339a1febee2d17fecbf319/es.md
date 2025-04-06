```
@spawn expr
```

Crea un cierre alrededor de una expresión y la ejecuta en un proceso elegido automáticamente, devolviendo un [`Future`](@ref) al resultado. Este macro está en desuso; se debe usar `@spawnat :any expr` en su lugar.

# Ejemplos

```julia-repl
julia> addprocs(3);

julia> f = @spawn myid()
Future(2, 1, 5, nothing)

julia> fetch(f)
2

julia> f = @spawn myid()
Future(3, 1, 7, nothing)

julia> fetch(f)
3
```

!!! compat "Julia 1.3"
    A partir de Julia 1.3, este macro está en desuso. Usa `@spawnat :any` en su lugar.

