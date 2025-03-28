```
@NamedTuple{key1::Type1, key2::Type2, ...}
@NamedTuple begin key1::Type1; key2::Type2; ...; end
```

Dieses Makro bietet eine bequemere Syntax zur Deklaration von `NamedTuple`-Typen. Es gibt einen `NamedTuple`-Typ mit den angegebenen Schlüsseln und Typen zurück, der äquivalent zu `NamedTuple{(:key1, :key2, ...), Tuple{Type1,Type2,...}}` ist. Wenn die `::Type`-Deklaration weggelassen wird, wird sie als `Any` betrachtet. Die `begin ... end`-Form ermöglicht es, die Deklarationen über mehrere Zeilen zu verteilen (ähnlich einer `struct`-Deklaration), ist aber ansonsten äquivalent. Das `NamedTuple`-Makro wird verwendet, wenn `NamedTuple`-Typen z.B. im REPL ausgegeben werden.

Zum Beispiel hat das Tupel `(a=3.1, b="hello")` einen Typ `NamedTuple{(:a, :b), Tuple{Float64, String}}`, der auch über `@NamedTuple` wie folgt deklariert werden kann:

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
    Dieses Makro ist seit Julia 1.5 verfügbar.

