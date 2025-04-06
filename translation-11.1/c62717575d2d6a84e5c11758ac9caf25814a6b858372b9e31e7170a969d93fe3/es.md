```
retry(f;  delays=ExponentialBackOff(), check=nothing) -> Function
```

Devuelve una función anónima que llama a la función `f`. Si se produce una excepción, `f` se vuelve a llamar repetidamente, cada vez que `check` devuelve `true`, después de esperar el número de segundos especificado en `delays`. `check` debe ingresar el estado actual de `delays` y la `Exception`.

!!! compat "Julia 1.2"
    Antes de Julia 1.2, esta firma estaba restringida a `f::Function`.


# Ejemplos

```julia
retry(f, delays=fill(5.0, 3))
retry(f, delays=rand(5:10, 2))
retry(f, delays=Base.ExponentialBackOff(n=3, first_delay=5, max_delay=1000))
retry(http_get, check=(s,e)->e.status == "503")(url)
retry(read, check=(s,e)->isa(e, IOError))(io, 128; all=false)
```
