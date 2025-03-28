```
AssertionError([msg])
```

La condición afirmada no se evaluó como `true`. El argumento opcional `msg` es una cadena de error descriptiva.

# Ejemplos

```jldoctest
julia> @assert false "esto no es verdad"
ERROR: AssertionError: esto no es verdad
```

`AssertionError` generalmente se lanza desde [`@assert`](@ref). ```
