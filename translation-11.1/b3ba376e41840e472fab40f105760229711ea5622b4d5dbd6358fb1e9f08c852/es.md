```
ord(lt, by, rev::Union{Bool, Nothing}, order::Ordering=Forward)
```

Construye un objeto [`Ordering`](@ref) a partir de los mismos argumentos utilizados por [`sort!`](@ref). Los elementos se transforman primero mediante la función `by` (que puede ser [`identity`](@ref)) y luego se comparan de acuerdo con la función `lt` o un orden existente `order`. `lt` debe ser [`isless`](@ref) o una función que obedezca las mismas reglas que el parámetro `lt` de [`sort!`](@ref). Finalmente, el orden resultante se invierte si `rev=true`.

No se permite pasar un `lt` diferente de `isless` junto con un `order` diferente de [`Base.Order.Forward`](@ref) o [`Base.Order.Reverse`](@ref); de lo contrario, todas las opciones son independientes y se pueden usar juntas en todas las combinaciones posibles.
