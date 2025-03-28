```
isdisjoint(x)
```

Crea una función que compara su argumento con `x` usando [`isdisjoint`](@ref), es decir, una función equivalente a `y -> isdisjoint(y, x)`. La función devuelta es de tipo `Base.Fix2{typeof(isdisjoint)}`, que se puede usar para implementar métodos especializados.

!!! compat "Julia 1.11"
    Esta funcionalidad requiere al menos Julia 1.11.

