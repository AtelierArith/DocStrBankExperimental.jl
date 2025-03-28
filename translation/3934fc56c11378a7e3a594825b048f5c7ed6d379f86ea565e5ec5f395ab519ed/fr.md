```
@NamedTuple{key1::Type1, key2::Type2, ...}
@NamedTuple begin key1::Type1; key2::Type2; ...; end
```

Cette macro offre une syntaxe plus pratique pour déclarer des types `NamedTuple`. Elle renvoie un type `NamedTuple` avec les clés et types donnés, équivalent à `NamedTuple{(:key1, :key2, ...), Tuple{Type1,Type2,...}}`. Si la déclaration `::Type` est omise, elle est considérée comme `Any`. La forme `begin ... end` permet de répartir les déclarations sur plusieurs lignes (similaire à une déclaration `struct`), mais est autrement équivalente. La macro `NamedTuple` est utilisée lors de l'impression des types `NamedTuple` dans par exemple le REPL.

Par exemple, le tuple `(a=3.1, b="hello")` a un type `NamedTuple{(:a, :b), Tuple{Float64, String}}`, qui peut également être déclaré via `@NamedTuple` comme suit :

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
    Cette macro est disponible depuis Julia 1.5.

