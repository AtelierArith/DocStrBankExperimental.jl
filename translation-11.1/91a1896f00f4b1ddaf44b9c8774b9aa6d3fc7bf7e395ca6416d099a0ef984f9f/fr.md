```
@views expression
```

Convertir chaque opération de découpage de tableau dans l'expression donnée (qui peut être un bloc `begin`/`end`, une boucle, une fonction, etc.) pour retourner une vue. Les indices scalaires, les types non-tableau et les appels explicites de [`getindex`](@ref) (par opposition à `array[...]`) ne sont pas affectés.

De même, `@views` convertit les tranches de chaînes en vues de [`SubString`](@ref).

!!! note
    La macro `@views` n'affecte que les expressions `array[...]` qui apparaissent explicitement dans l'expression donnée, pas le découpage de tableau qui se produit dans les fonctions appelées par ce code.


!!! compat "Julia 1.5"
    L'utilisation de `begin` dans une expression d'indexation pour se référer au premier index a été implémentée dans Julia 1.4, mais n'était prise en charge par `@views` qu'à partir de Julia 1.5.


# Exemples

```jldoctest
julia> A = zeros(3, 3);

julia> @views for row in 1:3
           b = A[row, :] # b est une vue, pas une copie
           b .= row      # assigner chaque élément à l'indice de ligne
       end

julia> A
3×3 Matrix{Float64}:
 1.0  1.0  1.0
 2.0  2.0  2.0
 3.0  3.0  3.0
```
