```
asin(A::AbstractMatrix)
```

Calcula el seno inverso de una matriz cuadrada `A`.

Si `A` es simétrica o hermítica, se utiliza su descomposición en valores propios ([`eigen`](@ref)) para calcular el seno inverso. De lo contrario, el seno inverso se determina utilizando [`log`](@ref) y [`sqrt`](@ref). Para la teoría y las fórmulas logarítmicas utilizadas para calcular esta función, consulte [^AH16_2].

[^AH16_2]: Mary Aprahamian y Nicholas J. Higham, "Funciones Trigonométricas Inversas de Matrices y Funciones Hiperbólicas Inversas: Teoría y Algoritmos", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# Ejemplos

```julia-repl
julia> asin(sin([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5-4.16334e-17im  0.1-5.55112e-17im
 -0.2+9.71445e-17im  0.3-1.249e-16im
```
