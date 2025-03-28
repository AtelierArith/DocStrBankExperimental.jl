```
*(A, B::AbstractMatrix, C)
A * B * C * D
```

La multiplicación encadenada de 3 o 4 matrices se realiza en la secuencia más eficiente, basada en los tamaños de los arreglos. Es decir, se compara el número de multiplicaciones escalares necesarias para `(A * B) * C` (con 3 matrices densas) con el de `A * (B * C)` para elegir cuál de estas ejecutar.

Si el último factor es un vector, o el primero un vector transpuesto, entonces es eficiente tratar con estos primero. En particular, `x' * B * y` significa `(x' * B) * y` para una `B::Matrix` ordinaria en orden de columna. A diferencia de `dot(x, B, y)`, esto asigna un arreglo intermedio.

Si el primer o último factor es un número, esto se fusionará con la multiplicación de matrices, utilizando [`mul!`](@ref) de 5 argumentos.

Véase también [`muladd`](@ref), [`dot`](@ref).

!!! compat "Julia 1.7"
    Estas optimizaciones requieren al menos Julia 1.7.

