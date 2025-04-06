```
@spawnat p expr
```

Crea un cierre alrededor de una expresión y ejecuta el cierre de manera asíncrona en el proceso `p`. Devuelve un [`Future`](@ref) al resultado. Si `p` es el símbolo literal citado `:any`, entonces el sistema elegirá automáticamente un procesador para usar.

# Ejemplos

```julia-repl
julia> addprocs(3);

julia> f = @spawnat 2 myid()
Future(2, 1, 3, nothing)

julia> fetch(f)
2

julia> f = @spawnat :any myid()
Future(3, 1, 7, nothing)

julia> fetch(f)
3
```

!!! compat "Julia 1.3"
    El argumento `:any` está disponible a partir de Julia 1.3.

