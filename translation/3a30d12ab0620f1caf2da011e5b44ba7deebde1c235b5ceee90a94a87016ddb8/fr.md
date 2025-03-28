```
invmod(n::Integer, T) where {T <: Base.BitInteger}
invmod(n::T) where {T <: Base.BitInteger}
```

Calcule l'inverse modulaire de `n` dans l'anneau des entiers de type `T`, c'est-à-dire modulo `2^N` où `N = 8*sizeof(T)` (par exemple `N = 32` pour `Int32`). En d'autres termes, ces méthodes satisfont les identités suivantes :

```
n * invmod(n) == 1
(n * invmod(n, T)) % T == 1
(n % T) * invmod(n, T) == 1
```

Notez que `*` ici est la multiplication modulaire dans l'anneau des entiers, `T`.

Spécifier le module impliqué par un type entier comme une valeur explicite est souvent peu pratique puisque le module est par définition trop grand pour être représenté par le type.

L'inverse modulaire est calculé de manière beaucoup plus efficace que le cas général en utilisant l'algorithme décrit dans https://arxiv.org/pdf/2204.04342.pdf.

!!! compat "Julia 1.11"
    Les méthodes `invmod(n)` et `invmod(n, T)` nécessitent Julia 1.11 ou une version ultérieure.

