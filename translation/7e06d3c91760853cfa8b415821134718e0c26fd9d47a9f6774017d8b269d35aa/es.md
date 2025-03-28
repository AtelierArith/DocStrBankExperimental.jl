```
merge(a::NamedTuple, bs::NamedTuple...)
```

Construye un nuevo tuple nombrado al fusionar dos o más existentes, de manera asociativa a la izquierda. La fusión procede de izquierda a derecha, entre pares de tuples nombrados, y por lo tanto el orden de los campos presentes en los tuples nombrados más a la izquierda y más a la derecha ocupa la misma posición que se encuentra en el tuple nombrado más a la izquierda. Sin embargo, los valores se toman de los campos coincidentes en el tuple nombrado más a la derecha que contiene ese campo. Los campos presentes solo en el tuple nombrado más a la derecha de un par se añaden al final. Se implementa un fallback para cuando solo se suministra un solo tuple nombrado, con la firma `merge(a::NamedTuple)`.

!!! compat "Julia 1.1"
    La fusión de 3 o más `NamedTuple` requiere al menos Julia 1.1.


# Ejemplos

```jldoctest
julia> merge((a=1, b=2, c=3), (b=4, d=5))
(a = 1, b = 4, c = 3, d = 5)
```

```jldoctest
julia> merge((a=1, b=2), (b=3, c=(d=1,)), (c=(d=2,),))
(a = 1, b = 3, c = (d = 2,))
```
