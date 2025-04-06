```
trsyl!(transa, transb, A, B, C, isgn=1) -> (C, scale)
```

Resuelve la ecuación matricial de Sylvester `A * X +/- X * B = scale*C` donde `A` y `B` son ambos cuasi-triangulares superiores. Si `transa = N`, `A` no se modifica. Si `transa = T`, `A` se transpone. Si `transa = C`, `A` se transpone conjugadamente. De manera similar para `transb` y `B`. Si `isgn = 1`, se resuelve la ecuación `A * X + X * B = scale * C`. Si `isgn = -1`, se resuelve la ecuación `A * X - X * B = scale * C`.

Devuelve `X` (sobrescribiendo `C`) y `scale`.
