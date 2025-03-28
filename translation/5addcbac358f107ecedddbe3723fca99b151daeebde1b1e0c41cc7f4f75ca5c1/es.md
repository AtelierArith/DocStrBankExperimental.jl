```
spr!(uplo, α, x, AP)
```

Actualiza la matriz `A` como `A+α*x*x'`, donde `A` es una matriz simétrica proporcionada en formato empaquetado `AP` y `x` es un vector.

Con `uplo = 'U'`, el arreglo AP debe contener la parte triangular superior de la matriz simétrica empaquetada secuencialmente, columna por columna, de modo que `AP[1]` contenga `A[1, 1]`, `AP[2]` y `AP[3]` contengan `A[1, 2]` y `A[2, 2]` respectivamente, y así sucesivamente.

Con `uplo = 'L'`, el arreglo AP debe contener la parte triangular inferior de la matriz simétrica empaquetada secuencialmente, columna por columna, de modo que `AP[1]` contenga `A[1, 1]`, `AP[2]` y `AP[3]` contengan `A[2, 1]` y `A[3, 1]` respectivamente, y así sucesivamente.

La entrada escalar `α` debe ser real.

Las entradas de arreglo `x` y `AP` deben ser todas de tipo `Float32` o `Float64`. Devuelve el `AP` actualizado.

!!! compat "Julia 1.8"
    `spr!` requiere al menos Julia 1.8.

