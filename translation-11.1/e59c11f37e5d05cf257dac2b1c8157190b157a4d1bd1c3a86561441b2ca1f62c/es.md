```
@show exs...
```

Imprime una o más expresiones, y sus resultados, en `stdout`, y devuelve el último resultado.

Véase también: [`show`](@ref), [`@info`](@ref man-logging), [`println`](@ref).

# Ejemplos

```jldoctest
julia> x = @show 1+2
1 + 2 = 3
3

julia> @show x^2 x/2;
x ^ 2 = 9
x / 2 = 1.5
```
