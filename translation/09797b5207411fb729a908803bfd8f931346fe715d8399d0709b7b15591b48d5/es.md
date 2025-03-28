```
stack(f, args...; [dims])
```

Aplica una función a cada elemento de una colección y `apila` el resultado. O a varias colecciones, que se han [`zip`](@ref)peado juntas.

La función debe devolver arreglos (o tuplas, o otros iteradores) todos del mismo tamaño. Estos se convierten en secciones del resultado, cada una separada a lo largo de `dims` (si se proporciona) o por defecto a lo largo de las últimas dimensiones.

Véase también [`mapslices`](@ref), [`eachcol`](@ref).

# Ejemplos

```jldoctest
julia> stack(c -> (c, c-32), "julia")
2×5 Matrix{Char}:
 'j'  'u'  'l'  'i'  'a'
 'J'  'U'  'L'  'I'  'A'

julia> stack(eachrow([1 2 3; 4 5 6]), (10, 100); dims=1) do row, n
         vcat(row, row .* n, row ./ n)
       end
2×9 Matrix{Float64}:
 1.0  2.0  3.0   10.0   20.0   30.0  0.1   0.2   0.3
 4.0  5.0  6.0  400.0  500.0  600.0  0.04  0.05  0.06
```
