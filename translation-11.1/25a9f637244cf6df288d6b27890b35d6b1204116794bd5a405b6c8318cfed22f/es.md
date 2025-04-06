```
hypot(x, y)
```

Calcula la hipotenusa $\sqrt{|x|^2+|y|^2}$ evitando desbordamiento y subdesbordamiento.

Este código es una implementación del algoritmo descrito en: Un algoritmo mejorado para `hypot(a,b)` por Carlos F. Borges. El artículo está disponible en línea en arXiv en el enlace https://arxiv.org/abs/1904.09481

```
hypot(x...)
```

Calcula la hipotenusa $\sqrt{\sum |x_i|^2}$ evitando desbordamiento y subdesbordamiento.

Consulta también `norm` en la biblioteca estándar [`LinearAlgebra`](@ref man-linalg).

# Ejemplos

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> a = Int64(10)^10;

julia> hypot(a, a)
1.4142135623730951e10

julia> √(a^2 + a^2) # a^2 desborda
ERROR: DomainError with -2.914184810805068e18:
sqrt fue llamado con un argumento real negativo pero solo devolverá un resultado complejo si se llama con un argumento complejo. Intenta sqrt(Complex(x)).
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
