```
binomial(n::Integer, k::Integer)
```

Der *binomiale Koeffizient* $\binom{n}{k}$ ist der Koeffizient des $k$-ten Terms in der polynomialen Expansion von $(1+x)^n$.

Wenn $n$ nicht negativ ist, dann ist es die Anzahl der Möglichkeiten, `k` aus `n` Elementen auszuwählen:

$$
\binom{n}{k} = \frac{n!}{k! (n-k)!}
$$

wobei $n!$ die [`factorial`](@ref) Funktion ist.

Wenn $n$ negativ ist, dann wird es in Bezug auf die Identität definiert

$$
\binom{n}{k} = (-1)^k \binom{k-n-1}{k}
$$

Siehe auch [`factorial`](@ref).

# Beispiele

```jldoctest
julia> binomial(5, 3)
10

julia> factorial(5) ÷ (factorial(5-3) * factorial(3))
10

julia> binomial(-5, 3)
-35
```

# Externe Links

  * [Binomialkoeffizient](https://en.wikipedia.org/wiki/Binomial_coefficient) auf Wikipedia.
