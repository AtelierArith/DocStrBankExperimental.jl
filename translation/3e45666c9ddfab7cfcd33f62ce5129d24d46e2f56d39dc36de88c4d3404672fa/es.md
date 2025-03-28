```
treewalk(f, tree::GitTree, post::Bool=false)
```

Recorre las entradas en `tree` y sus subárboles en orden post o pre. El orden pre significa comenzar en la raíz y luego recorrer el subárbol más a la izquierda (y recursivamente hacia abajo a través de los subárboles más a la izquierda de ese subárbol) y moverse a la derecha a través de los subárboles. El orden post significa comenzar en la parte inferior del subárbol más a la izquierda, recorrer hacia arriba a través de él, luego recorrer el siguiente subárbol a la derecha (nuevamente comenzando desde la parte inferior) y finalmente visitar la raíz del árbol al final.

El parámetro de función `f` debe tener la siguiente firma:

```
(String, GitTreeEntry) -> Cint
```

Un valor negativo devuelto de `f` detiene el recorrido del árbol. Un valor positivo significa que la entrada se omitirá si `post` es `false`.
