```
asin(A::AbstractMatrix)
```

Bir kare matris `A`'nın ters matris sinüsünü hesaplar.

Eğer `A` simetrik veya Hermit ise, ters sinüs hesaplamak için özdekompozisyon ([`eigen`](@ref)) kullanılır. Aksi takdirde, ters sinüs [`log`](@ref) ve [`sqrt`](@ref) kullanılarak belirlenir. Bu fonksiyonu hesaplamak için kullanılan teori ve logaritmik formüller için bkz. [^AH16_2].

[^AH16_2]: Mary Aprahamian ve Nicholas J. Higham, "Matrix Inverse Trigonometric and Inverse Hyperbolic Functions: Theory and Algorithms", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# Örnekler

```julia-repl
julia> asin(sin([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5-4.16334e-17im  0.1-5.55112e-17im
 -0.2+9.71445e-17im  0.3-1.249e-16im
```
