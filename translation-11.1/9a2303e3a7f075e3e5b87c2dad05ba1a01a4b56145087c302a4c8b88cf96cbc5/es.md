```
hash(x[, h::UInt]) -> UInt
```

Calcula un código hash entero tal que `isequal(x,y)` implica `hash(x)==hash(y)`. El segundo argumento opcional `h` es otro código hash que se mezcla con el resultado.

Los nuevos tipos deben implementar la forma de 2 argumentos, típicamente llamando al método `hash` de 2 argumentos de forma recursiva para mezclar los hashes de los contenidos entre sí (y con `h`). Típicamente, cualquier tipo que implemente `hash` también debería implementar su propio [`==`](@ref) (de ahí [`isequal`](@ref)) para garantizar la propiedad mencionada anteriormente.

El valor hash puede cambiar cuando se inicia un nuevo proceso de Julia.

```jldoctest
julia> a = hash(10)
0x95ea2955abd45275

julia> hash(10, a) # solo usa la salida de otra función hash como segundo argumento
0xd42bad54a8575b16
```

Ver también: [`objectid`](@ref), [`Dict`](@ref), [`Set`](@ref).
