```
annotations(str::Union{AnnotatedString, SubString{AnnotatedString}},
            [position::Union{Integer, UnitRange}]) ->
    Vector{@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}}

`str`에 적용되는 모든 주석을 가져옵니다. `position`이 제공되면, `position`과 겹치는 주석만 반환됩니다.

주석은 적용되는 영역과 함께 제공되며, 영역–주석 튜플의 벡터 형태로 제공됩니다.

[`AnnotatedString`](@ref)에서 문서화된 의미론에 따라 반환된 주석의 순서는 적용된 순서와 일치합니다.

또한: [`annotate!`](@ref).
```
