```
gcdx(a, b)
```

Berechnet den größten gemeinsamen (positiven) Teiler von `a` und `b` sowie deren Bézout-Koeffizienten, d.h. die ganzzahligen Koeffizienten `u` und `v`, die die Gleichung $ua+vb = d = gcd(a, b)$ erfüllen. $gcdx(a, b)$ gibt $(d, u, v)$ zurück.

Die Argumente können ganze und rationale Zahlen sein.

!!! compat "Julia 1.4"
    Rationale Argumente erfordern Julia 1.4 oder höher.


# Beispiele

```jldoctest
julia> gcdx(12, 42)
(6, -3, 1)

julia> gcdx(240, 46)
(2, -9, 47)
```

!!! note
    Bézout-Koeffizienten sind *nicht* eindeutig definiert. `gcdx` gibt die minimalen Bézout-Koeffizienten zurück, die durch den erweiterten euklidischen Algorithmus berechnet werden. (Ref: D. Knuth, TAoCP, 2/e, S. 325, Algorithmus X.) Für vorzeichenbehaftete ganze Zahlen sind diese Koeffizienten `u` und `v` minimal im Sinne, dass $|u| < |b/d|$ und $|v| < |a/d|$. Darüber hinaus werden die Vorzeichen von `u` und `v` so gewählt, dass `d` positiv ist. Für vorzeichenlose ganze Zahlen könnten die Koeffizienten `u` und `v` nahe ihrem `typemax` liegen, und die Identität gilt dann nur über die Modulo-Arithmetik der vorzeichenlosen ganzen Zahlen.

