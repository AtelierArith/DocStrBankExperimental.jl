```
isequal(x)
```

Crea una función que compara su argumento con `x` utilizando [`isequal`](@ref), es decir, una función equivalente a `y -> isequal(y, x)`.

La función devuelta es de tipo `Base.Fix2{typeof(isequal)}`, que se puede utilizar para implementar métodos especializados.
