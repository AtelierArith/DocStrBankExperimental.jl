```
set_num_threads(n::Integer)
set_num_threads(::Nothing)
```

Establece el número de hilos que la biblioteca BLAS debe usar igual a `n::Integer`.

También acepta `nothing`, en cuyo caso julia intenta adivinar el número predeterminado de hilos. Pasar `nothing` no se recomienda y existe principalmente por razones históricas.
