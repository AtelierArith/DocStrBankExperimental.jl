```
donde
```

La palabra clave `where` crea un tipo [`UnionAll`](@ref), que puede considerarse como una unión iterada de otros tipos, sobre todos los valores de alguna variable. Por ejemplo, `Vector{T} where T<:Real` incluye todos los [`Vector`](@ref)s donde el tipo de elemento es algún tipo de número `Real`.

El límite de la variable se establece de forma predeterminada en [`Any`](@ref) si se omite:

```julia
Vector{T} where T    # abreviatura de `where T<:Any`
```

Las variables también pueden tener límites inferiores:

```julia
Vector{T} where T>:Int
Vector{T} where Int<:T<:Real
```

También hay una sintaxis concisa para expresiones `where` anidadas. Por ejemplo, esto:

```julia
Pair{T, S} where S<:Array{T} where T<:Number
```

se puede acortar a:

```julia
Pair{T, S} where {T<:Number, S<:Array{T}}
```

Esta forma se encuentra a menudo en las firmas de métodos.

Ten en cuenta que en esta forma, las variables se enumeran de afuera hacia adentro. Esto coincide con el orden en el que se sustituyen las variables cuando un tipo se "aplica" a valores de parámetros utilizando la sintaxis `T{p1, p2, ...}`.
