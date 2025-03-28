```
∉(item, collection) -> Bool
∌(collection, item) -> Bool
```

Negación de `∈` y `∋`, es decir, verifica que `item` no esté en `collection`.

Al hacer broadcasting con `items .∉ collection`, tanto `item` como `collection` se transmiten, lo cual a menudo no es lo que se pretende. Por ejemplo, si ambos argumentos son vectores (y las dimensiones coinciden), el resultado es un vector que indica si cada valor en `collection` `items` no está en el valor en la posición correspondiente en `collection`. Para obtener un vector que indique si cada valor en `items` no está en `collection`, envuelve `collection` en una tupla o un `Ref` así: `items .∉ Ref(collection)`.

# Ejemplos

```jldoctest
julia> 1 ∉ 2:4
true

julia> 1 ∉ 1:3
false

julia> [1, 2] .∉ [2, 3]
2-element BitVector:
 1
 1

julia> [1, 2] .∉ ([2, 3],)
2-element BitVector:
 1
 0
```
