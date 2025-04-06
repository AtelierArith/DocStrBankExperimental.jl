```
redirect_stdio(f; stdin=nothing, stderr=nothing, stdout=nothing)
```

Redirige un subconjunto de los flujos `stdin`, `stderr`, `stdout`, llama a `f()` y restaura cada flujo.

Los valores posibles para cada flujo son:

  * `nothing` indicando que el flujo no debe ser redirigido.
  * `path::AbstractString` redirigiendo el flujo al archivo en `path`.
  * `io` un `IOStream`, `TTY`, [`Pipe`](@ref), socket, o `devnull`.

# Ejemplos

```julia-repl
julia> redirect_stdio(stdout="stdout.txt", stderr="stderr.txt") do
           print("hello stdout")
           print(stderr, "hello stderr")
       end

julia> read("stdout.txt", String)
"hello stdout"

julia> read("stderr.txt", String)
"hello stderr"
```

# Casos extremos

Es posible pasar el mismo argumento a `stdout` y `stderr`:

```julia-repl
julia> redirect_stdio(stdout="log.txt", stderr="log.txt", stdin=devnull) do
    ...
end
```

Sin embargo, no se admite pasar dos descriptores distintos del mismo archivo.

```julia-repl
julia> io1 = open("same/path", "w")

julia> io2 = open("same/path", "w")

julia> redirect_stdio(f, stdout=io1, stderr=io2) # no soportado
```

Además, el argumento `stdin` no puede ser el mismo descriptor que `stdout` o `stderr`.

```julia-repl
julia> io = open(...)

julia> redirect_stdio(f, stdout=io, stdin=io) # no soportado
```

!!! compat "Julia 1.7"
    `redirect_stdio` requiere Julia 1.7 o posterior.

