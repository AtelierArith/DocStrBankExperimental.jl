```
@views expresión
```

Convierte cada operación de corte de matriz en la expresión dada (que puede ser un bloque `begin`/`end`, un bucle, una función, etc.) para que devuelva una vista. Los índices escalares, los tipos no de matriz y las llamadas explícitas a [`getindex`](@ref) (en lugar de `array[...]`) no se ven afectados.

De manera similar, `@views` convierte los cortes de cadenas en vistas de [`SubString`](@ref).

!!! nota
    El macro `@views` solo afecta las expresiones `array[...]` que aparecen explícitamente en la expresión dada, no el corte de matriz que ocurre en funciones llamadas por ese código.


!!! compat "Julia 1.5"
    Usar `begin` en una expresión de indexación para referirse al primer índice se implementó en Julia 1.4, pero solo fue compatible con `@views` a partir de Julia 1.5.


# Ejemplos

```jldoctest
julia> A = zeros(3, 3);

julia> @views for row in 1:3
           b = A[row, :] # b es una vista, no una copia
           b .= row      # asigna cada elemento al índice de fila
       end

julia> A
3×3 Matrix{Float64}:
 1.0  1.0  1.0
 2.0  2.0  2.0
 3.0  3.0  3.0
```
