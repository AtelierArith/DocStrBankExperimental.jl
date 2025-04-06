```
normalize!(a::AbstractArray, p::Real=2)
```

Normaliza el arreglo `a` en su lugar para que su `p`-norma sea igual a la unidad, es decir, `norm(a, p) == 1`. Consulta también [`normalize`](@ref) y [`norm`](@ref).
