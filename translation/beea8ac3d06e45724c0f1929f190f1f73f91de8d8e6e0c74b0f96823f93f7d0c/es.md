```
fma(x, y, z)
```

Calcula `x*y+z` sin redondear el resultado intermedio `x*y`. En algunos sistemas, esto es significativamente más costoso que `x*y+z`. `fma` se utiliza para mejorar la precisión en ciertos algoritmos. Consulta [`muladd`](@ref).
