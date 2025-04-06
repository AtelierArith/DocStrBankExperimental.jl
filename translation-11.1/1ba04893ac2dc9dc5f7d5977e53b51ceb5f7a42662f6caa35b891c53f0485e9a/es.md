```
LinearAlgebra.peakflops(n::Integer=4096; eltype::DataType=Float64, ntrials::Integer=3, parallel::Bool=false)
```

`peakflops` calcula la tasa máxima de flops de la computadora utilizando precisión doble [`gemm!`](@ref LinearAlgebra.BLAS.gemm!). Por defecto, si no se especifican argumentos, multiplica dos matrices `Float64` de tamaño `n x n`, donde `n = 4096`. Si el BLAS subyacente utiliza múltiples hilos, se logran tasas de flops más altas. El número de hilos de BLAS se puede establecer con [`BLAS.set_num_threads(n)`](@ref).

Si se proporciona el argumento de palabra clave `eltype`, `peakflops` construirá matrices con elementos del tipo `eltype` para calcular la tasa máxima de flops.

Por defecto, `peakflops` utilizará el mejor tiempo de 3 pruebas. Si se proporciona el argumento de palabra clave `ntrials`, `peakflops` utilizará esa cantidad de pruebas para elegir el mejor tiempo.

Si el argumento de palabra clave `parallel` se establece en `true`, `peakflops` se ejecuta en paralelo en todos los procesadores de trabajo. Se devuelve la tasa de flops de toda la computadora paralela. Al ejecutarse en paralelo, solo se utiliza 1 hilo de BLAS. El argumento `n` sigue refiriéndose al tamaño del problema que se resuelve en cada procesador.

!!! compat "Julia 1.1"
    Esta función requiere al menos Julia 1.1. En Julia 1.0 está disponible en la biblioteca estándar `InteractiveUtils`.

