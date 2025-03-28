```
last(coll)
```

Obtiene el último elemento de una colección ordenada, si se puede calcular en O(1) tiempo. Esto se logra llamando a [`lastindex`](@ref) para obtener el último índice. Devuelve el punto final de un [`AbstractRange`](@ref) incluso si está vacío.

Véase también [`first`](@ref), [`endswith`](@ref).

# Ejemplos

```jldoctest
julia> last(1:2:10)
9

julia> last([1; 2; 3; 4])
4
```
