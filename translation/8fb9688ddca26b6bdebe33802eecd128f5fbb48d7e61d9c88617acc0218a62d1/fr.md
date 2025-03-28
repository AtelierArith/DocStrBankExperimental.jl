```
binomial(x::Number, k::Integer)
```

Le coefficient binomial généralisé, défini pour `k ≥ 0` par le polynôme

$$
\frac{1}{k!} \prod_{j=0}^{k-1} (x - j)
$$

Lorsque `k < 0`, il renvoie zéro.

Pour le cas de `x` entier, cela équivaut au coefficient binomial entier ordinaire

$$
\binom{n}{k} = \frac{n!}{k! (n-k)!}
$$

D'autres généralisations à des `k` non entiers sont mathématiquement possibles, mais impliquent la fonction Gamma et/ou la fonction bêta, qui ne sont pas fournies par la bibliothèque standard de Julia mais sont disponibles dans des packages externes tels que [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl).

# Liens externes

  * [Coefficient binomial](https://en.wikipedia.org/wiki/Binomial_coefficient) sur Wikipedia.
