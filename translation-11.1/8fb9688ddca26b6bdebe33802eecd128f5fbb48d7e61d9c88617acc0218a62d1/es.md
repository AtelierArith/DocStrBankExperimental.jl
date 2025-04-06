```
binomial(x::Number, k::Integer)
```

El coeficiente binomial generalizado, definido para `k ≥ 0` por el polinomio

$$
\frac{1}{k!} \prod_{j=0}^{k-1} (x - j)
$$

Cuando `k < 0` devuelve cero.

Para el caso de `x` entero, esto es equivalente al coeficiente binomial entero ordinario

$$
\binom{n}{k} = \frac{n!}{k! (n-k)!}
$$

Generalizaciones adicionales a `k` no entero son matemáticamente posibles, pero implican la función Gamma y/o la función beta, que no están proporcionadas por la biblioteca estándar de Julia, pero están disponibles en paquetes externos como [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl).

# Enlaces externos

  * [Coeficiente binomial](https://es.wikipedia.org/wiki/Coeficiente_binomial) en Wikipedia.
