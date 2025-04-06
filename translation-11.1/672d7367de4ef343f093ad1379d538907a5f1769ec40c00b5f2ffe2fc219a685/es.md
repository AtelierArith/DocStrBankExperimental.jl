```
@printf([io::IO], "%Fmt", args...)
```

Imprime `args` utilizando una cadena de especificación de formato al estilo de `printf` de C. Opcionalmente, se puede pasar un `IO` como primer argumento para redirigir la salida.

# Ejemplos

```jldoctest
julia> @printf "Hello %s" "world"
Hello world

julia> @printf "Scientific notation %e" 1.234
Scientific notation 1.234000e+00

julia> @printf "Scientific notation three digits %.3e" 1.23456
Scientific notation three digits 1.235e+00

julia> @printf "Decimal two digits %.2f" 1.23456
Decimal two digits 1.23

julia> @printf "Padded to length 5 %5i" 123
Padded to length 5   123

julia> @printf "Padded with zeros to length 6 %06i" 123
Padded with zeros to length 6 000123

julia> @printf "Use shorter of decimal or scientific %g %g" 1.23 12300000.0
Use shorter of decimal or scientific 1.23 1.23e+07

julia> @printf "Use dynamic width and precision  %*.*f" 10 2 0.12345
Use dynamic width and precision        0.12
```

Para una especificación sistemática del formato, consulta [aquí](https://en.cppreference.com/w/c/io/fprintf). También consulta [`@sprintf`](@ref) para obtener el resultado como un `String` en lugar de que se imprima.

# Advertencias

`Inf` y `NaN` se imprimen consistentemente como `Inf` y `NaN` para los flags `%a`, `%A`, `%e`, `%E`, `%f`, `%F`, `%g`, y `%G`. Además, si un número de punto flotante está igualmente cerca de los valores numéricos de dos posibles cadenas de salida, se elige la cadena de salida más alejada de cero.

# Ejemplos

```jldoctest
julia> @printf("%f %F %f %F", Inf, Inf, NaN, NaN)
Inf Inf NaN NaN

julia> @printf "%.0f %.1f %f" 0.5 0.025 -0.0078125
0 0.0 -0.007812
```

!!! compat "Julia 1.8"
    A partir de Julia 1.8, los anchos de `%s` (cadena) y `%c` (carácter) se calculan utilizando [`textwidth`](@ref), que por ejemplo ignora caracteres de ancho cero (como los caracteres combinados para marcas diacríticas) y trata ciertos caracteres "anchos" (por ejemplo, emoji) como ancho `2`.


!!! compat "Julia 1.10"
    Los especificadores de ancho dinámico como `%*s` y `%0*.*f` requieren Julia 1.10.

