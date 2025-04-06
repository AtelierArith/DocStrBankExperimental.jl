```
reflect!(x, y, c, s)
```

Écrase `x` avec `c*x + s*y` et `y` avec `conj(s)*x - c*y`. Renvoie `x` et `y`.

!!! compat "Julia 1.5"
    `reflect!` nécessite au moins Julia 1.5.

