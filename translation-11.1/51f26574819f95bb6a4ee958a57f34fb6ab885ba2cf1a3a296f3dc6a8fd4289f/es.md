```
acos(A::AbstractMatrix)
```

Calcula el coseno inverso de una matriz cuadrada `A`.

Si `A` es simétrica o hermítica, se utiliza su descomposición en valores propios ([`eigen`](@ref)) para calcular el coseno inverso. De lo contrario, el coseno inverso se determina utilizando [`log`](@ref) y [`sqrt`](@ref). Para la teoría y las fórmulas logarítmicas utilizadas para calcular esta función, consulte [^AH16_1].

[^AH16_1]: Mary Aprahamian y Nicholas J. Higham, "Funciones Trigonométricas Inversas de Matrices y Funciones Hiperbólicas Inversas: Teoría y Algoritmos", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# Ejemplos

```julia-repl
julia> acos(cos([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5-8.32667e-17im  0.1+0.0im
 -0.2+2.63678e-16im  0.3-3.46945e-16im
```
