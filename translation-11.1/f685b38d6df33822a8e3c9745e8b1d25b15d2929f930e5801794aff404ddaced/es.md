```
acquire(f, s::Semaphore)
```

Ejecuta `f` después de adquirir del Semáforo `s`, y `release` al completar o en caso de error.

Por ejemplo, una forma de bloque do que asegura que solo 2 llamadas a `foo` estarán activas al mismo tiempo:

```julia
s = Base.Semaphore(2)
@sync for _ in 1:100
    Threads.@spawn begin
        Base.acquire(s) do
            foo()
        end
    end
end
```

!!! compat "Julia 1.8"
    Este método requiere al menos Julia 1.8.

