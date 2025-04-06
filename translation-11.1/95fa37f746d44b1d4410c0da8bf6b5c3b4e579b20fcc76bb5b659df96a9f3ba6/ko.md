```
AnnotatedChar{S <: AbstractChar} <: AbstractChar
```

주석이 있는 문자입니다.

보다 구체적으로, 이는 래핑된 문자와 함께 임의의 레이블이 있는 주석 목록(`@NamedTuple{label::Symbol, value}`)을 보유하는 다른 [`AbstractChar`](@ref) 주위의 간단한 래퍼입니다.

또한 참조: [`AnnotatedString`](@ref), [`annotatedstring`](@ref), `annotations`, 및 `annotate!`.

# 생성자

```julia
AnnotatedChar(s::S) -> AnnotatedChar{S}
AnnotatedChar(s::S, annotations::Vector{@NamedTuple{label::Symbol, value}})
```

# 예제

```julia-repl
julia> AnnotatedChar('j', :label => 1)
'j': ASCII/Unicode U+006A (category Ll: Letter, lowercase)
```
