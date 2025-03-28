```
randsubseq([rng=default_rng(),] A, p) -> Vector
```

Gibt einen Vektor zurück, der aus einer zufälligen Teilfolge des gegebenen Arrays `A` besteht, wobei jedes Element von `A` (in der Reihenfolge) mit einer unabhängigen Wahrscheinlichkeit `p` einbezogen wird. (Die Komplexität ist linear in `p*length(A)`, sodass diese Funktion auch dann effizient ist, wenn `p` klein und `A` groß ist.) Technisch wird dieser Prozess als "Bernoulli-Stichprobe" von `A` bezeichnet.

# Beispiele

```jldoctest
julia> randsubseq(Xoshiro(123), 1:8, 0.3)
2-element Vector{Int64}:
 4
 7
```
