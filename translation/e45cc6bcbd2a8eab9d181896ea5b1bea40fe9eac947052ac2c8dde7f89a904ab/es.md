```
opnorm(A::Adjoint{<:Any,<:AbstractVector}, q::Real=2)
opnorm(A::Transpose{<:Any,<:AbstractVector}, q::Real=2)
```

Para vectores envueltos en Adjoint/Transpose, devuelve el operador $q$-norm de `A`, que es equivalente al `p`-norm con valor `p = q/(q-1)`. Coinciden en `p = q = 2`. Usa [`norm`](@ref) para calcular el `p` norm de `A` como un vector.

La diferencia en la norma entre un espacio vectorial y su dual surge para preservar la relación entre dualidad y el producto punto, y el resultado es consistente con el operador `p`-norm de una matriz `1 × n`.

# Ejemplos

```jldoctest
julia> v = [1; im];

julia> vc = v';

julia> opnorm(vc, 1)
1.0

julia> norm(vc, 1)
2.0

julia> norm(v, 1)
2.0

julia> opnorm(vc, 2)
1.4142135623730951

julia> norm(vc, 2)
1.4142135623730951

julia> norm(v, 2)
1.4142135623730951

julia> opnorm(vc, Inf)
2.0

julia> norm(vc, Inf)
1.0

julia> norm(v, Inf)
1.0
```
