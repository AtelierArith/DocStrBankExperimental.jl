```
similar(storagetype, axes)
```

Crée un tableau mutable non initialisé analogue à celui spécifié par `storagetype`, mais avec `axes` spécifié par le dernier argument.

**Exemples** :

```
similar(Array{Int}, axes(A))
```

crée un tableau qui "agit comme" un `Array{Int}` (et qui pourrait en effet être soutenu par un), mais qui est indexé de manière identique à `A`. Si `A` a un indexage conventionnel, cela sera identique à `Array{Int}(undef, size(A))`, mais si `A` a un indexage non conventionnel, alors les indices du résultat correspondront à ceux de `A`.

```
similar(BitArray, (axes(A, 2),))
```

créerait un tableau logique unidimensionnel dont les indices correspondent à ceux des colonnes de `A`.
