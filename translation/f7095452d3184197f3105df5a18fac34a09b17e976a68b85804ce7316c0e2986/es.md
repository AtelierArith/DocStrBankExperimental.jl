```
similar(storagetype, axes)
```

Crea un arreglo mutable no inicializado análogo al especificado por `storagetype`, pero con `axes` especificados por el último argumento.

**Ejemplos**:

```
similar(Array{Int}, axes(A))
```

crea un arreglo que "actúa como" un `Array{Int}` (y que de hecho podría estar respaldado por uno), pero que está indexado de manera idéntica a `A`. Si `A` tiene indexación convencional, esto será idéntico a `Array{Int}(undef, size(A))`, pero si `A` tiene indexación no convencional, entonces los índices del resultado coincidirán con los de `A`.

```
similar(BitArray, (axes(A, 2),))
```

crearía un arreglo lógico unidimensional cuyos índices coinciden con los de las columnas de `A`.
