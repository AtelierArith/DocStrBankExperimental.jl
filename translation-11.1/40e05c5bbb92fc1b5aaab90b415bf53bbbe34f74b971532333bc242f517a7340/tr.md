```
annotatedstring(values...)
```

Herhangi bir sayıda `values` kullanarak bir `AnnotatedString` oluşturur ve bunların [`print`](@ref) edilmiş temsilini kullanır.

Bu, [`string`](@ref) gibi çalışır, ancak mevcut olan herhangi bir notasyonu ([`AnnotatedString`](@ref) veya [`AnnotatedChar`](@ref) değerleri şeklinde) korumaya özen gösterir.

Ayrıca bkz. [`AnnotatedString`](@ref) ve [`AnnotatedChar`](@ref).

## Örnekler

```julia-repl
julia> annotatedstring("şimdi bir AnnotatedString")
"şimdi bir AnnotatedString"

julia> annotatedstring(AnnotatedString("notlu", [(1:9, :label => 1)]), ", ve notsuz")
"notlu, ve notsuz"
```
