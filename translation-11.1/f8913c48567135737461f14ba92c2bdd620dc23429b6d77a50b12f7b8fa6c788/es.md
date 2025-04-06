```
to_indices(A, I::Tuple)
```

Convierte la tupla `I` en una tupla de índices para su uso en la indexación del arreglo `A`.

La tupla devuelta debe contener solo `Int`s o `AbstractArray`s de índices escalares que son compatibles con el arreglo `A`. Generará un error al encontrar un tipo de índice novedoso que no sabe cómo procesar.

Para tipos de índice simples, se delega a la función no exportada `Base.to_index(A, i)` para procesar cada índice `i`. Aunque esta función interna no está destinada a ser llamada directamente, `Base.to_index` puede ser extendida por tipos de arreglo o índice personalizados para proporcionar comportamientos de indexación personalizados.

Los tipos de índice más complicados pueden requerir más contexto sobre la dimensión en la que indexan. Para apoyar esos casos, `to_indices(A, I)` llama a `to_indices(A, axes(A), I)`, que luego recorre recursivamente tanto la tupla dada de índices como los índices dimensionales de `A` en conjunto. Como tal, no se garantiza que todos los tipos de índice se propaguen a `Base.to_index`.

# Ejemplos

```jldoctest
julia> A = zeros(1,2,3,4);

julia> to_indices(A, (1,1,2,2))
(1, 1, 2, 2)

julia> to_indices(A, (1,1,2,20)) # sin verificación de límites
(1, 1, 2, 20)

julia> to_indices(A, (CartesianIndex((1,)), 2, CartesianIndex((3,4)))) # índice exótico
(1, 2, 3, 4)

julia> to_indices(A, ([1,1], 1:2, 3, 4))
([1, 1], 1:2, 3, 4)

julia> to_indices(A, (1,2)) # sin verificación de forma
(1, 2)
```
