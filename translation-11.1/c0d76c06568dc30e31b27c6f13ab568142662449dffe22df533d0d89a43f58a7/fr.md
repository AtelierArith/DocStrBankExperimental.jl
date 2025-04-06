```
binomial(n::Integer, k::Integer)
```

Le *coefficient binomial* $\binom{n}{k}$, étant le coefficient du $k$ème terme dans l'expansion polynomiale de $(1+x)^n$.

Si $n$ est non négatif, alors c'est le nombre de façons de choisir `k` parmi `n` éléments :

$$
\binom{n}{k} = \frac{n!}{k! (n-k)!}
$$

où $n!$ est la fonction [`factorial`](@ref).

Si $n$ est négatif, alors il est défini en termes de l'identité

$$
\binom{n}{k} = (-1)^k \binom{k-n-1}{k}
$$

Voir aussi [`factorial`](@ref).

# Exemples

```jldoctest
julia> binomial(5, 3)
10

julia> factorial(5) ÷ (factorial(5-3) * factorial(3))
10

julia> binomial(-5, 3)
-35
```

# Liens externes

  * [Coefficient binomial](https://en.wikipedia.org/wiki/Binomial_coefficient) sur Wikipedia.
