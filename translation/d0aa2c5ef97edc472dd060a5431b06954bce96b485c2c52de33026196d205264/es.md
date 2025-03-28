```
>(x)
```

Crea una función que compara su argumento con `x` usando [`>`](@ref), es decir, una función equivalente a `y -> y > x`. La función devuelta es de tipo `Base.Fix2{typeof(>)}`, que se puede usar para implementar métodos especializados.

!!! compat "Julia 1.2"
    Esta funcionalidad requiere al menos Julia 1.2.

