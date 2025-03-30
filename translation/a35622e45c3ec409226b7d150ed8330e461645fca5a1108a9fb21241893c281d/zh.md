```
annotations(str::Union{AnnotatedString, SubString{AnnotatedString}},
            [position::Union{Integer, UnitRange}]) ->
    Vector{@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}}
```

获取适用于 `str` 的所有注释。如果提供了 `position`，则仅返回与 `position` 重叠的注释。

注释与其适用的区域一起提供，以区域–注释元组的向量形式。

根据 [`AnnotatedString`](@ref) 中记录的语义，返回的注释顺序与它们被应用的顺序相匹配。

另见: [`annotate!`](@ref).
