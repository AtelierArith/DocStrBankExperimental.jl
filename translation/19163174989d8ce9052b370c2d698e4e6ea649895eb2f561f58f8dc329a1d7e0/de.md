```
set_num_threads(n::Integer)
set_num_threads(::Nothing)
```

Setzen Sie die Anzahl der Threads, die die BLAS-Bibliothek verwenden soll, gleich `n::Integer`.

Akzeptiert auch `nothing`, in diesem Fall versucht Julia, die Standardanzahl der Threads zu erraten. Das Übergeben von `nothing` wird nicht empfohlen und existiert hauptsächlich aus historischen Gründen.
