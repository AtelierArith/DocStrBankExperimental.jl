```
atan(A::AbstractMatrix)
```

Calcula la tangente inversa de una matriz cuadrada `A`.

Si `A` es simétrica o hermítica, se utiliza su descomposición en valores propios ([`eigen`](@ref)) para calcular la tangente inversa. De lo contrario, la tangente inversa se determina utilizando [`log`](@ref). Para la teoría y las fórmulas logarítmicas utilizadas para calcular esta función, consulte [^AH16_3].

[^AH16_3]: Mary Aprahamian y Nicholas J. Higham, "Funciones Trigonométricas Inversas de Matrices y Funciones Hiperbólicas Inversas: Teoría y Algoritmos", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# Ejemplos

```julia-repl
julia> atan(tan([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5+1.38778e-17im  0.1-2.77556e-17im
 -0.2+6.93889e-17im  0.3-4.16334e-17im
```
