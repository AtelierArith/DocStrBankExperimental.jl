```
@NamedTuple{key1::Type1, key2::Type2, ...}
@NamedTuple begin key1::Type1; key2::Type2; ...; end
```

Este macro proporciona una sintaxis más conveniente para declarar tipos `NamedTuple`. Devuelve un tipo `NamedTuple` con las claves y tipos dados, equivalente a `NamedTuple{(:key1, :key2, ...), Tuple{Type1,Type2,...}}`. Si se omite la declaración `::Type`, se toma como `Any`. La forma `begin ... end` permite que las declaraciones se dividan en múltiples líneas (similar a una declaración de `struct`), pero es equivalente de otro modo. El macro `NamedTuple` se utiliza al imprimir tipos `NamedTuple` en, por ejemplo, el REPL.

Por ejemplo, la tupla `(a=3.1, b="hello")` tiene un tipo `NamedTuple{(:a, :b), Tuple{Float64, String}}`, que también se puede declarar a través de `@NamedTuple` como:

```jldoctest
julia> @NamedTuple{a::Float64, b::String}
@NamedTuple{a::Float64, b::String}

julia> @NamedTuple begin
           a::Float64
           b::String
       end
@NamedTuple{a::Float64, b::String}
```

!!! compat "Julia 1.5"
    Este macro está disponible desde Julia 1.5.

