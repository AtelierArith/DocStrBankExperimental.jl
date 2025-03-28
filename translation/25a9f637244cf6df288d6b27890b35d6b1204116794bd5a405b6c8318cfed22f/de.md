```
hypot(x, y)
```

Berechne die Hypotenuse $\sqrt{|x|^2+|y|^2}$ und vermeide Überlauf und Unterlauf.

Dieser Code ist eine Implementierung des Algorithmus, der in: An Improved Algorithm for `hypot(a,b)` von Carlos F. Borges beschrieben ist. Der Artikel ist online auf arXiv unter dem Link   https://arxiv.org/abs/1904.09481 verfügbar.

```
hypot(x...)
```

Berechne die Hypotenuse $\sqrt{\sum |x_i|^2}$ und vermeide Überlauf und Unterlauf.

Siehe auch `norm` in der [`LinearAlgebra`](@ref man-linalg) Standardbibliothek.

# Beispiele

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> a = Int64(10)^10;

julia> hypot(a, a)
1.4142135623730951e10

julia> √(a^2 + a^2) # a^2 überläuft
ERROR: DomainError with -2.914184810805068e18:
sqrt wurde mit einem negativen reellen Argument aufgerufen, gibt aber nur ein komplexes Ergebnis zurück, wenn es mit einem komplexen Argument aufgerufen wird. Versuche sqrt(Complex(x)).
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
