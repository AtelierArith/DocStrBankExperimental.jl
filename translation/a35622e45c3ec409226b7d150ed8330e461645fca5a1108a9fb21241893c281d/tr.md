```
annotations(str::Union{AnnotatedString, SubString{AnnotatedString}},
            [position::Union{Integer, UnitRange}]) ->
    Vector{@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}}

`str` için geçerli olan tüm notları alın. `position` sağlanırsa, yalnızca `position` ile örtüşen notlar döndürülecektir.

Notlar, uygulandıkları bölgelerle birlikte, bölge–not çiftleri şeklinde bir vektör olarak sağlanır.

[`AnnotatedString`](@ref) belgelerinde belgelenen anlamlara uygun olarak, döndürülen notların sırası, uygulandıkları sırayı yansıtır.

Ayrıca bkz: [`annotate!`](@ref).
```
