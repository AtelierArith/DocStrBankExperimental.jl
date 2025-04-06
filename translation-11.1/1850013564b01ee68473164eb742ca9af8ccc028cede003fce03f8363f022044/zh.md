```
Unicode.julia_chartransform(c::Union{Char,Integer})
```

将Unicode字符（`Char`）或代码点（`Integer`）`c`映射到相应的“等效”字符或代码点，具体取决于Julia解析器中使用的自定义等价（除了NFC规范化之外）。

例如，`'µ'`（U+00B5 微）在Julia的解析器中被视为等同于`'μ'`（U+03BC 迈），因此`julia_chartransform`执行此转换，同时保持其他字符不变：

```jldoctest
julia> Unicode.julia_chartransform('µ')
'μ': Unicode U+03BC (category Ll: Letter, lowercase)

julia> Unicode.julia_chartransform('x')
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)
```

`julia_chartransform`主要用于传递给[`Unicode.normalize`](@ref)函数，以模仿Julia解析器使用的规范化：

```jldoctest
julia> s = "µö"
"µö"

julia> s2 = Unicode.normalize(s, compose=true, stable=true, chartransform=Unicode.julia_chartransform)
"μö"

julia> collect(s2)
2-element Vector{Char}:
 'μ': Unicode U+03BC (category Ll: Letter, lowercase)
 'ö': Unicode U+00F6 (category Ll: Letter, lowercase)

julia> s2 == string(Meta.parse(s))
true
```

!!! compat "Julia 1.8"
    此函数在Julia 1.8中引入。

