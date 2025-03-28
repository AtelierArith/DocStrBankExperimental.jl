```
in!(x, s::AbstractSet) -> Bool
```

Si `x` está en `s`, devuelve `true`. Si no, agrega `x` a `s` y devuelve `false`. Esto es equivalente a `in(x, s) ? true : (push!(s, x); false)`, pero puede tener una implementación más eficiente.

Véase también: [`in`](@ref), [`push!`](@ref), [`Set`](@ref)

!!! compat "Julia 1.11"
    Esta función requiere al menos 1.11.


# Ejemplos

```jldoctest; filter = r"^  [1234]$"
julia> s = Set{Any}([1, 2, 3]); in!(4, s)
false

julia> length(s)
4

julia> in!(0x04, s)
true

julia> s
Set{Any} con 4 elementos:
  4
  2
  3
  1
```
