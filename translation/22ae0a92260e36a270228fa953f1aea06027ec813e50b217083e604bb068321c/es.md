```
reduce(op, itr; [init])
```

Reduce la colección dada `itr` con el operador binario dado `op`. Si se proporciona, el valor inicial `init` debe ser un elemento neutro para `op` que se devolverá para colecciones vacías. No se especifica si `init` se utiliza para colecciones no vacías.

Para colecciones vacías, proporcionar `init` será necesario, excepto en algunos casos especiales (por ejemplo, cuando `op` es uno de `+`, `*`, `max`, `min`, `&`, `|`) cuando Julia puede determinar el elemento neutro de `op`.

Las reducciones para ciertos operadores de uso común pueden tener implementaciones especiales y deben usarse en su lugar: [`maximum`](@ref)`(itr)`, [`minimum`](@ref)`(itr)`, [`sum`](@ref)`(itr)`, [`prod`](@ref)`(itr)`, [`any`](@ref)`(itr)`, [`all`](@ref)`(itr)`. Hay métodos eficientes para concatenar ciertos arreglos de arreglos llamando a `reduce(`[`vcat`](@ref)`, arr)` o `reduce(`[`hcat`](@ref)`, arr)`.

La asociatividad de la reducción depende de la implementación. Esto significa que no puedes usar operaciones no asociativas como `-` porque no está definido si `reduce(-,[1,2,3])` debe evaluarse como `(1-2)-3` o `1-(2-3)`. Usa [`foldl`](@ref) o [`foldr`](@ref) en su lugar para garantizar la asociatividad izquierda o derecha.

Algunas operaciones acumulan error. El paralelismo será más fácil si la reducción se puede ejecutar en grupos. Las futuras versiones de Julia podrían cambiar el algoritmo. Ten en cuenta que los elementos no se reordenan si usas una colección ordenada.

# Ejemplos

```jldoctest
julia> reduce(*, [2; 3; 4])
24

julia> reduce(*, [2; 3; 4]; init=-1)
-24
```
