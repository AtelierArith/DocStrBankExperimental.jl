```
evalpoly(x, p)
```

Bewerten Sie das Polynom $\sum_k x^{k-1} p[k]$ für die Koeffizienten `p[1]`, `p[2]`, ...; das heißt, die Koeffizienten sind in aufsteigender Reihenfolge nach der Potenz von `x` angegeben. Schleifen werden zur Compile-Zeit entrollt, wenn die Anzahl der Koeffizienten statisch bekannt ist, d.h. wenn `p` ein `Tuple` ist. Diese Funktion generiert effizienten Code unter Verwendung der Horner-Methode, wenn `x` reell ist, oder unter Verwendung eines Goertzel-ähnlichen [^DK62] Algorithmus, wenn `x` komplex ist.

[^DK62]: Donald Knuth, Art of Computer Programming, Volume 2: Seminumerical Algorithms, Sec. 4.6.4.

!!! compat "Julia 1.4"
    Diese Funktion erfordert Julia 1.4 oder später.


# Beispiele

```jldoctest
julia> evalpoly(2, (1, 2, 3))
17
```
