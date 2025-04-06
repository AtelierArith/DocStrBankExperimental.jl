```
Stateful(itr)
```

Hay varias formas diferentes de pensar en este envoltorio de iterador:

1. Proporciona un envoltorio mutable alrededor de un iterador y su estado de iteración.
2. Convierte una abstracción similar a un iterador en una abstracción similar a un `Channel`.
3. Es un iterador que se muta para convertirse en su propio iterador de resto cada vez que se produce un elemento.

`Stateful` proporciona la interfaz de iterador regular. Al igual que otros iteradores mutables (por ejemplo, [`Base.Channel`](@ref)), si la iteración se detiene prematuramente (por ejemplo, mediante un [`break`](@ref) en un bucle [`for`](@ref)), la iteración se puede reanudar desde el mismo lugar al continuar iterando sobre el mismo objeto iterador (en contraste, un iterador inmutable se reiniciaría desde el principio).

# Ejemplos

```jldoctest
julia> a = Iterators.Stateful("abcdef");

julia> isempty(a)
false

julia> popfirst!(a)
'a': ASCII/Unicode U+0061 (categoría Ll: Letra, minúscula)

julia> collect(Iterators.take(a, 3))
3-element Vector{Char}:
 'b': ASCII/Unicode U+0062 (categoría Ll: Letra, minúscula)
 'c': ASCII/Unicode U+0063 (categoría Ll: Letra, minúscula)
 'd': ASCII/Unicode U+0064 (categoría Ll: Letra, minúscula)

julia> collect(a)
2-element Vector{Char}:
 'e': ASCII/Unicode U+0065 (categoría Ll: Letra, minúscula)
 'f': ASCII/Unicode U+0066 (categoría Ll: Letra, minúscula)

julia> Iterators.reset!(a); popfirst!(a)
'a': ASCII/Unicode U+0061 (categoría Ll: Letra, minúscula)

julia> Iterators.reset!(a, "hello"); popfirst!(a)
'h': ASCII/Unicode U+0068 (categoría Ll: Letra, minúscula)
```

```jldoctest
julia> a = Iterators.Stateful([1,1,1,2,3,4]);

julia> for x in a; x == 1 || break; end

julia> peek(a)
3

julia> sum(a) # Sumar los elementos restantes
7
```
