```
hypot(x, y)
```

Hipotenüsü hesaplar $\sqrt{|x|^2+|y|^2}$ taşma ve alt taşmayı önleyerek.

Bu kod, Carlos F. Borges tarafından tanımlanan `hypot(a,b)` algoritmasının bir uygulamasıdır. Makale çevrimiçi olarak arXiv'de şu bağlantıda mevcuttur: https://arxiv.org/abs/1904.09481

```
hypot(x...)
```

Hipotenüsü hesaplar $\sqrt{\sum |x_i|^2}$ taşma ve alt taşmayı önleyerek.

Ayrıca `norm`'u [`LinearAlgebra`](@ref man-linalg) standart kütüphanesinde görebilirsiniz.

# Örnekler

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> a = Int64(10)^10;

julia> hypot(a, a)
1.4142135623730951e10

julia> √(a^2 + a^2) # a^2 taşar
HATA: DomainError with -2.914184810805068e18:
sqrt negatif bir reel argüman ile çağrıldı, ancak yalnızca karmaşık bir argüman ile çağrıldığında karmaşık bir sonuç döndürecektir. sqrt(Complex(x)) ile denemeyi deneyin.
Stacktrace:
[...]

julia> hypot(3, 4im)
5.0

julia> hypot(-5.7)
5.7

julia> hypot(3, 4im, 12.0)
13.0

julia> using LinearAlgebra

julia> norm([a, a, a, a]) == hypot(a, a, a, a)
true
```
