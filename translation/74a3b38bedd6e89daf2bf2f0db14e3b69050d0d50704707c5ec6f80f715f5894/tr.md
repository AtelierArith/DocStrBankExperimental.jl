```
log(A::AbstractMatrix)
```

Eğer `A` negatif gerçek özdeğere sahip değilse, `A`'nın ana matris logaritmasını hesaplayın, yani $e^X = A$ ve $-\pi < Im(\lambda) < \pi$ koşulunu sağlayan, `X` matrisinin benzersiz matrisini hesaplayın; burada `X`'in tüm özdeğerleri $\lambda$'dır. Eğer `A`'nın negatif veya sıfır özdeğerleri varsa, mümkün olduğunda bir ana olmayan matris fonksiyonu döndürülür.

Eğer `A` simetrik veya Hermit ise, özdeğişimi ([`eigen`](@ref)) kullanılır, eğer `A` üçgen bir matris ise, ters ölçekleme ve kare alma yönteminin geliştirilmiş bir versiyonu uygulanır (bkz. [^AH12] ve [^AHR13]). Eğer `A` negatif özdeğere sahip olmayan gerçek bir matris ise, gerçek Schur formu hesaplanır. Aksi takdirde, karmaşık Schur formu hesaplanır. Daha sonra, [^AHR13]’teki üst (kuazi-) üçgen algoritması, üst (kuazi-) üçgen faktör üzerinde kullanılır.

[^AH12]: Awad H. Al-Mohy ve Nicholas J. Higham, "Matris logaritması için geliştirilmiş ters ölçekleme ve kare alma algoritmaları", SIAM Journal on Scientific Computing, 34(4), 2012, C153-C169. [doi:10.1137/110852553](https://doi.org/10.1137/110852553)

[^AHR13]: Awad H. Al-Mohy, Nicholas J. Higham ve Samuel D. Relton, "Matris logaritmasının Fréchet türevini hesaplama ve koşul sayısını tahmin etme", SIAM Journal on Scientific Computing, 35(4), 2013, C394-C410. [doi:10.1137/120885991](https://doi.org/10.1137/120885991)

# Örnekler

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
