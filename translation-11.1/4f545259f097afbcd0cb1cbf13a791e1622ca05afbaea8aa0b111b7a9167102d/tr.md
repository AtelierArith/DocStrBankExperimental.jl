```
atan(A::AbstractMatrix)
```

Bir kare matris `A`'nın ters matris tanjantını hesaplar.

Eğer `A` simetrik veya Hermit ise, ters tanjantı hesaplamak için özdeğişim ([`eigen`](@ref)) kullanılır. Aksi takdirde, ters tanjant [`log`](@ref) kullanılarak belirlenir. Bu fonksiyonu hesaplamak için kullanılan teori ve logaritmik formüller için bkz. [^AH16_3].

[^AH16_3]: Mary Aprahamian ve Nicholas J. Higham, "Matris Ters Trigonometrik ve Ters Hiperbolik Fonksiyonlar: Teori ve Algoritmalar", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# Örnekler

```julia-repl
julia> atan(tan([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5+1.38778e-17im  0.1-2.77556e-17im
 -0.2+6.93889e-17im  0.3-4.16334e-17im
```
