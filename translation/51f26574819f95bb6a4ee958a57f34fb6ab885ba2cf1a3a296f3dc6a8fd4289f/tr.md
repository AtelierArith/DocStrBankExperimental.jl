```
acos(A::AbstractMatrix)
```

Bir kare matris `A`'nın ters matris kosinüsünü hesaplar.

Eğer `A` simetrik veya Hermit ise, ters kosinüs hesaplamak için özdeğişim ([`eigen`](@ref)) kullanılır. Aksi takdirde, ters kosinüs [`log`](@ref) ve [`sqrt`](@ref) kullanılarak belirlenir. Bu fonksiyonu hesaplamak için kullanılan teori ve logaritmik formüller için bkz. [^AH16_1].

[^AH16_1]: Mary Aprahamian ve Nicholas J. Higham, "Matrix Inverse Trigonometric and Inverse Hyperbolic Functions: Theory and Algorithms", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# Örnekler

```julia-repl
julia> acos(cos([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5-8.32667e-17im  0.1+0.0im
 -0.2+2.63678e-16im  0.3-3.46945e-16im
```
