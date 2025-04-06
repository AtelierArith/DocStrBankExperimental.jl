```
evalpoly(x, p)
```

Évalue le polynôme $\sum_k x^{k-1} p[k]$ pour les coefficients `p[1]`, `p[2]`, ...; c'est-à-dire que les coefficients sont donnés dans l'ordre croissant par puissance de `x`. Les boucles sont déroulées au moment de la compilation si le nombre de coefficients est statiquement connu, c'est-à-dire lorsque `p` est un `Tuple`. Cette fonction génère du code efficace en utilisant la méthode de Horner si `x` est réel, ou en utilisant un algorithme de type Goertzel [^DK62] si `x` est complexe.

[^DK62]: Donald Knuth, Art of Computer Programming, Volume 2: Seminumerical Algorithms, Sec. 4.6.4.

!!! compat "Julia 1.4"
    Cette fonction nécessite Julia 1.4 ou une version ultérieure.


# Exemples

```jldoctest
julia> evalpoly(2, (1, 2, 3))
17
```
