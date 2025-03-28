```
LinearAlgebra.Givens(i1,i2,c,s) -> G
```

Un operador lineal de rotación de Givens. Los campos `c` y `s` representan el coseno y el seno del ángulo de rotación, respectivamente. El tipo `Givens` admite la multiplicación por la izquierda `G*A` y la multiplicación por la derecha con transposición conjugada `A*G'`. El tipo no tiene un `size` y, por lo tanto, se puede multiplicar con matrices de tamaño arbitrario siempre que `i2<=size(A,2)` para `G*A` o `i2<=size(A,1)` para `A*G'`.

Ver también [`givens`](@ref).
