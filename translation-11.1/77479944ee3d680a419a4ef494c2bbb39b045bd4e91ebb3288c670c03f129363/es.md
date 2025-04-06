```
pushdisplay(d::AbstractDisplay)
```

Empuja una nueva pantalla `d` en la parte superior de la pila de backend de visualización global. Llamar a `display(x)` o `display(mime, x)` mostrará `x` en el backend compatible más alto en la pila (es decir, el backend más alto que no lanza un [`MethodError`](@ref)).
