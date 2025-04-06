```
Base.isambiguous(m1, m2; ambiguous_bottom=false) -> Bool
```

Determina si dos métodos `m1` y `m2` pueden ser ambiguos para alguna firma de llamada. Esta prueba se realiza en el contexto de otros métodos de la misma función; de forma aislada, `m1` y `m2` podrían ser ambiguos, pero si se ha definido un tercer método que resuelve la ambigüedad, esto devuelve `false`. Alternativamente, de forma aislada `m1` y `m2` podrían estar ordenados, pero si un tercer método no puede ser ordenado con ellos, pueden causar una ambigüedad juntos.

Para tipos paramétricos, el argumento clave `ambiguous_bottom` controla si `Union{}` cuenta como una intersección ambigua de parámetros de tipo: cuando es `true`, se considera ambigua; cuando es `false`, no lo es.

# Ejemplos

```jldoctest
julia> foo(x::Complex{<:Integer}) = 1
foo (función genérica con 1 método)

julia> foo(x::Complex{<:Rational}) = 2
foo (función genérica con 2 métodos)

julia> m1, m2 = collect(methods(foo));

julia> typeintersect(m1.sig, m2.sig)
Tuple{typeof(foo), Complex{Union{}}}

julia> Base.isambiguous(m1, m2, ambiguous_bottom=true)
true

julia> Base.isambiguous(m1, m2, ambiguous_bottom=false)
false
```
