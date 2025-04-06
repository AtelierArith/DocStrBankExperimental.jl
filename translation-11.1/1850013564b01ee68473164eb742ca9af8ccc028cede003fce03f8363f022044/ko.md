```
Unicode.julia_chartransform(c::Union{Char,Integer})
```

유니코드 문자(`Char`) 또는 코드포인트(`Integer`) `c`를 줄리아 파서 내에서 사용되는 사용자 정의 동등성에 따라 해당 "동등한" 문자 또는 코드포인트로 매핑합니다(또한 NFC 정규화 포함).

예를 들어, `'µ'` (U+00B5 마이크로)는 줄리아의 파서에 의해 `'μ'` (U+03BC 뮤)와 동등하게 취급되므로, `julia_chartransform`은 다른 문자는 변경하지 않고 이 변환을 수행합니다:

```jldoctest
julia> Unicode.julia_chartransform('µ')
'μ': Unicode U+03BC (category Ll: Letter, lowercase)

julia> Unicode.julia_chartransform('x')
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)
```

`julia_chartransform`은 줄리아 파서에 의해 사용되는 정규화를 모방하기 위해 [`Unicode.normalize`](@ref) 함수에 전달하는 데 주로 유용합니다:

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
    이 함수는 Julia 1.8에서 도입되었습니다.

