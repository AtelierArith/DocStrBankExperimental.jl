```
unique!(A::AbstractVector)
```

Elimina los elementos duplicados según lo determinado por [`isequal`](@ref) y [`hash`](@ref), y luego devuelve el `A` modificado. `unique!` devolverá los elementos de `A` en el orden en que ocurren. Si no te importa el orden de los datos devueltos, entonces llamar a `(sort!(A); unique!(A))` será mucho más eficiente siempre que los elementos de `A` se puedan ordenar.

# Ejemplos

```jldoctest
julia> unique!([1, 1, 1])
1-element Vector{Int64}:
 1

julia> A = [7, 3, 2, 3, 7, 5];

julia> unique!(A)
4-element Vector{Int64}:
 7
 3
 2
 5

julia> B = [7, 6, 42, 6, 7, 42];

julia> sort!(B);  # unique! puede procesar datos ordenados de manera mucho más eficiente.

julia> unique!(B)
3-element Vector{Int64}:
  6
  7
 42
```
