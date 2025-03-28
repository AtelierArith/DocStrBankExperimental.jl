```
LinearAlgebra.peakflops(n::Integer=4096; eltype::DataType=Float64, ntrials::Integer=3, parallel::Bool=false)
```

`peakflops` berechnet die maximale Flop-Rate des Computers, indem es die doppelte Genauigkeit [`gemm!`](@ref LinearAlgebra.BLAS.gemm!) verwendet. Standardmäßig multipliziert es, wenn keine Argumente angegeben sind, zwei `Float64`-Matrizen der Größe `n x n`, wobei `n = 4096`. Wenn das zugrunde liegende BLAS mehrere Threads verwendet, werden höhere Flop-Raten erreicht. Die Anzahl der BLAS-Threads kann mit [`BLAS.set_num_threads(n)`](@ref) festgelegt werden.

Wenn das Schlüsselwort-Argument `eltype` angegeben ist, wird `peakflops` Matrizen mit Elementen des Typs `eltype` konstruieren, um die maximale Flop-Rate zu berechnen.

Standardmäßig verwendet `peakflops` die beste Zeit aus 3 Versuchen. Wenn das Schlüsselwort-Argument `ntrials` angegeben ist, verwendet `peakflops` so viele Versuche, um die beste Zeit auszuwählen.

Wenn das Schlüsselwort-Argument `parallel` auf `true` gesetzt ist, wird `peakflops` parallel auf allen Arbeitsprozessoren ausgeführt. Die Flop-Rate des gesamten parallelen Computers wird zurückgegeben. Bei der Ausführung in parallel wird nur 1 BLAS-Thread verwendet. Das Argument `n` bezieht sich weiterhin auf die Größe des Problems, das auf jedem Prozessor gelöst wird.

!!! compat "Julia 1.1"
    Diese Funktion erfordert mindestens Julia 1.1. In Julia 1.0 ist sie aus der Standardbibliothek `InteractiveUtils` verfügbar.

