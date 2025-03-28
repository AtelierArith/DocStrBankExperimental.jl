```
mientras
```

`mientras` los bucles evalúan repetidamente una expresión condicional y continúan evaluando el cuerpo del bucle mientras la expresión siga siendo verdadera. Si la expresión de condición es falsa cuando se alcanza por primera vez el bucle `mientras`, el cuerpo nunca se evalúa.

# Ejemplos

```jldoctest
julia> i = 1
1

julia> mientras i < 5
           println(i)
           global i += 1
       end
1
2
3
4
```
