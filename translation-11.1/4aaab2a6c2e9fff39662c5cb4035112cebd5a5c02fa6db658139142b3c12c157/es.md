```
hpmv!(uplo, α, AP, x, β, y)
```

Actualiza el vector `y` como `α*A*x + β*y`, donde `A` es una matriz Hermitiana proporcionada en formato empaquetado `AP`.

Con `uplo = 'U'`, el arreglo AP debe contener la parte triangular superior de la matriz Hermitiana empaquetada secuencialmente, columna por columna, de modo que `AP[1]` contenga `A[1, 1]`, `AP[2]` y `AP[3]` contengan `A[1, 2]` y `A[2, 2]` respectivamente, y así sucesivamente.

Con `uplo = 'L'`, el arreglo AP debe contener la parte triangular inferior de la matriz Hermitiana empaquetada secuencialmente, columna por columna, de modo que `AP[1]` contenga `A[1, 1]`, `AP[2]` y `AP[3]` contengan `A[2, 1]` y `A[3, 1]` respectivamente, y así sucesivamente.

Las entradas escalares `α` y `β` deben ser números complejos o reales.

Las entradas de arreglo `x`, `y` y `AP` deben ser todas del tipo `ComplexF32` o `ComplexF64`.

Devuelve el `y` actualizado.

!!! compat "Julia 1.5"
    `hpmv!` requiere al menos Julia 1.5.

