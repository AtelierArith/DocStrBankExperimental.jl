```
XPRS_BARORDER
```

Newton barrier: This controls the Cholesky factorization in the Newton-Barrier. (integer)

Default value: `0`

Values: 0 : Choose automatically. 1 : Minimum degree method. This selects diagonal elements with the smallest number of nonzeros in their rows or columns. 2 : Minimum local fill method. This considers the adjacency graph of nonzeros in the matrix and seeks to eliminate nodes that minimize the creation of new edges. 3 : Nested dissection method. This considers the adjacency graph and recursively seeks to separate it into non-adjacent pieces.
