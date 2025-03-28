```
@nref N A indexexpr
```

Generar expresiones como `A[i_1, i_2, ...]`. `indexexpr` puede ser un prefijo de símbolo de iteración, o una expresión de función anónima.

# Ejemplos

```jldoctest
julia> @macroexpand Base.Cartesian.@nref 3 A i
:(A[i_1, i_2, i_3])
```
