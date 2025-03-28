```
\(A, B)
```

División de matrices utilizando un polialgoritmo. Para las matrices de entrada `A` y `B`, el resultado `X` es tal que `A*X == B` cuando `A` es cuadrada. El solucionador que se utiliza depende de la estructura de `A`. Si `A` es triangular superior o inferior (o diagonal), no se requiere factorización de `A` y el sistema se resuelve con sustitución hacia adelante o hacia atrás. Para matrices cuadradas no triangulares, se utiliza una factorización LU.

Para `A` rectangular, el resultado es la solución de mínimos cuadrados de norma mínima calculada mediante una factorización QR con pivoteo de `A` y una estimación de rango de `A` basada en el factor R.

Cuando `A` es dispersa, se utiliza un polialgoritmo similar. Para matrices indefinidas, la factorización `LDLt` no utiliza pivoteo durante la factorización numérica y, por lo tanto, el procedimiento puede fallar incluso para matrices invertibles.

Ver también: [`factorize`](@ref), [`pinv`](@ref).

# Ejemplos

```jldoctest
julia> A = [1 0; 1 -2]; B = [32; -4];

julia> X = A \ B
2-element Vector{Float64}:
 32.0
 18.0

julia> A * X == B
true
```
