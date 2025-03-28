```
reflect!(x, y, c, s)
```

Überschreibt `x` mit `c*x + s*y` und `y` mit `conj(s)*x - c*y`. Gibt `x` und `y` zurück.

!!! compat "Julia 1.5"
    `reflect!` erfordert mindestens Julia 1.5.

