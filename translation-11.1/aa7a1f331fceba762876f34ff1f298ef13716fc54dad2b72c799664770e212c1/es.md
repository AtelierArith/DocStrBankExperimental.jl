```
tipo abstracto
```

`tipo abstracto` declara un tipo que no puede ser instanciado, y sirve solo como un nodo en el gráfico de tipos, describiendo así conjuntos de tipos concretos relacionados: aquellos tipos concretos que son sus descendientes. Los tipos abstractos forman la jerarquía conceptual que hace que el sistema de tipos de Julia sea más que solo una colección de implementaciones de objetos. Por ejemplo:

```julia
abstract type Number end
abstract type Real <: Number end
```

[`Number`](@ref) no tiene supertipo, mientras que [`Real`](@ref) es un subtipo abstracto de `Number`.
