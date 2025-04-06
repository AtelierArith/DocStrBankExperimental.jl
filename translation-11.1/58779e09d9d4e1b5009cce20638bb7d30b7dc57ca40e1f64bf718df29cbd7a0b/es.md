```
in(item, collection) -> Bool
∈(item, collection) -> Bool
```

Determina si un elemento está en la colección dada, en el sentido de que es [`==`](@ref) a uno de los valores generados al iterar sobre la colección. Devuelve un valor `Bool`, excepto si `item` es [`missing`](@ref) o `collection` contiene `missing` pero no `item`, en cuyo caso se devuelve `missing` ([lógica de tres valores](https://es.wikipedia.org/wiki/L%C3%B3gica_de_tres_valores), coincidiendo con el comportamiento de [`any`](@ref) y [`==`](@ref)).

Algunas colecciones siguen una definición ligeramente diferente. Por ejemplo, los [`Set`](@ref)s verifican si el elemento es [`isequal`](@ref) a uno de los elementos; los [`Dict`](@ref)s buscan pares `key=>value`, y la `key` se compara usando [`isequal`](@ref).

Para probar la presencia de una clave en un diccionario, usa [`haskey`](@ref) o `k in keys(dict)`. Para las colecciones mencionadas anteriormente, el resultado es siempre un `Bool`.

Al hacer broadcasting con `in.(items, collection)` o `items .∈ collection`, tanto `item` como `collection` se transmiten, lo cual a menudo no es lo que se pretende. Por ejemplo, si ambos argumentos son vectores (y las dimensiones coinciden), el resultado es un vector que indica si cada valor en la colección `items` está `in` el valor en la posición correspondiente en `collection`. Para obtener un vector que indique si cada valor en `items` está en `collection`, envuelve `collection` en una tupla o un `Ref` así: `in.(items, Ref(collection))` o `items .∈ Ref(collection)`.

Ver también: [`∉`](@ref), [`insorted`](@ref), [`contains`](@ref), [`occursin`](@ref), [`issubset`](@ref).

# Ejemplos

```jldoctest
julia> a = 1:3:20
1:3:19

julia> 4 in a
true

julia> 5 in a
false

julia> missing in [1, 2]
missing

julia> 1 in [2, missing]
missing

julia> 1 in [1, missing]
true

julia> missing in Set([1, 2])
false

julia> (1=>missing) in Dict(1=>10, 2=>20)
missing

julia> [1, 2] .∈ [2, 3]
2-element BitVector:
 0
 0

julia> [1, 2] .∈ ([2, 3],)
2-element BitVector:
 0
 1
```
