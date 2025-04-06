```
remotecall_fetch(f, id::Integer, args...; kwargs...)
```

Realiza `fetch(remotecall(...))` en un solo mensaje. Los argumentos de palabra clave, si los hay, se pasan a `f`. Cualquier excepción remota se captura en una [`RemoteException`](@ref) y se lanza.

Véase también [`fetch`](@ref) y [`remotecall`](@ref).

# Ejemplos

```julia-repl
$ julia -p 2

julia> remotecall_fetch(sqrt, 2, 4)
2.0

julia> remotecall_fetch(sqrt, 2, -4)
ERROR: En el trabajador 2:
DomainError con -4.0:
sqrt fue llamado con un argumento real negativo pero solo devolverá un resultado complejo si se llama con un argumento complejo. Intenta sqrt(Complex(x)).
...
```
