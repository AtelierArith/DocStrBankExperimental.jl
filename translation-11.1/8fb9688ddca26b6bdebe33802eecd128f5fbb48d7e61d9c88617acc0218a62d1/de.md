```
binomial(x::Number, k::Integer)
```

Der verallgemeinerte binomiale Koeffizient, definiert für `k ≥ 0` durch das Polynom

$$
\frac{1}{k!} \prod_{j=0}^{k-1} (x - j)
$$

Wenn `k < 0`, gibt es null zurück.

Im Fall von ganzzahligen `x` entspricht dies dem gewöhnlichen ganzzahligen binomialen Koeffizienten

$$
\binom{n}{k} = \frac{n!}{k! (n-k)!}
$$

Weitere Verallgemeinerungen für nicht-ganzzahlige `k` sind mathematisch möglich, beinhalten jedoch die Gammafunktion und/oder die Betafunktion, die nicht von der Julia-Standardbibliothek bereitgestellt werden, aber in externen Paketen wie [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl) verfügbar sind.

# Externe Links

  * [Binomialkoeffizient](https://de.wikipedia.org/wiki/Binomialkoeffizient) auf Wikipedia.
