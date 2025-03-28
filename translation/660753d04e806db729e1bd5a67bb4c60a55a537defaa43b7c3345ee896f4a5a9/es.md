```
issetequal(x)
```

Crea una función que compara su argumento con `x` utilizando [`issetequal`](@ref), es decir, una función equivalente a `y -> issetequal(y, x)`. La función devuelta es de tipo `Base.Fix2{typeof(issetequal)}`, que se puede utilizar para implementar métodos especializados.

!!! compat "Julia 1.11"
    Esta funcionalidad requiere al menos Julia 1.11.

