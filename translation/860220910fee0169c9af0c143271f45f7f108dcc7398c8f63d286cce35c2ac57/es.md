```
expm1(x)
```

Calcula con precisión $e^x-1$. Evita la pérdida de precisión involucrada en la evaluación directa de exp(x)-1 para valores pequeños de x.

# Ejemplos

```jldoctest
julia> expm1(1e-16)
1.0e-16

julia> exp(1e-16) - 1
0.0
```
