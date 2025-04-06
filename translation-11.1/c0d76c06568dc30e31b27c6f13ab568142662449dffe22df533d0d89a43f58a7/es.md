```
binomial(n::Integer, k::Integer)
```

El *coeficiente binomial* $\binom{n}{k}$, siendo el coeficiente del término $k$ en la expansión polinómica de $(1+x)^n$.

Si $n$ es no negativo, entonces es el número de maneras de elegir `k` de `n` elementos:

$$
\binom{n}{k} = \frac{n!}{k! (n-k)!}
$$

donde $n!$ es la función [`factorial`](@ref).

Si $n$ es negativo, entonces se define en términos de la identidad

$$
\binom{n}{k} = (-1)^k \binom{k-n-1}{k}
$$

Ver también [`factorial`](@ref).

# Ejemplos

```jldoctest
julia> binomial(5, 3)
10

julia> factorial(5) ÷ (factorial(5-3) * factorial(3))
10

julia> binomial(-5, 3)
-35
```

# Enlaces externos

  * [Coeficiente binomial](https://en.wikipedia.org/wiki/Binomial_coefficient) en Wikipedia.

```
