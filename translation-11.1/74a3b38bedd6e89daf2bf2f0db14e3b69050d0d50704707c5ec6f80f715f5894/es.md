```
log(A::AbstractMatrix)
```

Si `A` no tiene valores propios reales negativos, calcula el logaritmo matricial principal de `A`, es decir, la matriz única $X$ tal que $e^X = A$ y $-\pi < Im(\lambda) < \pi$ para todos los valores propios $\lambda$ de $X$. Si `A` tiene valores propios no positivos, se devuelve una función matricial no principal siempre que sea posible.

Si `A` es simétrica o hermítica, se utiliza su descomposición en valores propios ([`eigen`](@ref)), si `A` es triangular se emplea una versión mejorada del método de escalado inverso y cuadrado (ver [^AH12] y [^AHR13]). Si `A` es real sin valores propios negativos, entonces se calcula la forma de Schur real. De lo contrario, se calcula la forma de Schur compleja. Luego se utiliza el algoritmo triangular superior (cuasi-)triangular en [^AHR13] sobre el factor (cuasi-)triangular superior.

[^AH12]: Awad H. Al-Mohy y Nicholas J. Higham, "Algoritmos mejorados de escalado inverso y cuadrado para el logaritmo matricial", SIAM Journal on Scientific Computing, 34(4), 2012, C153-C169. [doi:10.1137/110852553](https://doi.org/10.1137/110852553)

[^AHR13]: Awad H. Al-Mohy, Nicholas J. Higham y Samuel D. Relton, "Computando la derivada de Fréchet del logaritmo matricial y estimando el número de condición", SIAM Journal on Scientific Computing, 35(4), 2013, C394-C410. [doi:10.1137/120885991](https://doi.org/10.1137/120885991)

# Ejemplos

```jldoctest
julia> A = Matrix(2.7182818*I, 2, 2)
2×2 Matrix{Float64}:
 2.71828  0.0
 0.0      2.71828

julia> log(A)
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
