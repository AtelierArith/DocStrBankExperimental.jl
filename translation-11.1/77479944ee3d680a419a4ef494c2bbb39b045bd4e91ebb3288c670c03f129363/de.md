```
pushdisplay(d::AbstractDisplay)
```

Schiebt ein neues Display `d` oben auf den globalen Display-Backend-Stack. Der Aufruf von `display(x)` oder `display(mime, x)` zeigt `x` auf dem obersten kompatiblen Backend im Stack an (d.h. dem obersten Backend, das keinen [`MethodError`](@ref) auslöst).
