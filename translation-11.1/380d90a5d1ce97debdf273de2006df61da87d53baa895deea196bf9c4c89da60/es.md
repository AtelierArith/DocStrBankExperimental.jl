```
@generated f
```

`@generated` se utiliza para anotar una función que será generada. En el cuerpo de la función generada, solo se pueden leer los tipos de los argumentos (no los valores). La función devuelve una expresión citada que se evalúa cuando se llama a la función. El macro `@generated` no debe usarse en funciones que mutan el ámbito global o dependen de elementos mutables.

Consulta [Metaprogramming](@ref) para más detalles.

# Ejemplos

```jldoctest
julia> @generated function bar(x)
           if x <: Integer
               return :(x ^ 2)
           else
               return :(x)
           end
       end
bar (generic function with 1 method)

julia> bar(4)
16

julia> bar("baz")
"baz"
```
