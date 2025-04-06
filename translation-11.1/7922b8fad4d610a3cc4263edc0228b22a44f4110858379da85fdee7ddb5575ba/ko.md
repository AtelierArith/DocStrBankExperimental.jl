```
titlecase(s::AbstractString; [wordsep::Function], strict::Bool=true) -> String
```

`s`의 각 단어의 첫 번째 문자를 대문자로 변환합니다. `strict`가 true인 경우, 나머지 문자는 소문자로 변환되며, 그렇지 않으면 변경되지 않습니다. 기본적으로 새로운 그래프를 시작하는 모든 비문자는 단어 구분자로 간주됩니다. 어떤 문자가 단어 구분자로 간주되어야 하는지를 결정하기 위해 `wordsep` 키워드로 프레디케이트를 전달할 수 있습니다. `s`의 첫 번째 문자만 대문자로 변환하려면 [`uppercasefirst`](@ref)도 참조하십시오.

또한 [`uppercase`](@ref), [`lowercase`](@ref), [`uppercasefirst`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> titlecase("the JULIA programming language")
"The Julia Programming Language"

julia> titlecase("ISS - international space station", strict=false)
"ISS - International Space Station"

julia> titlecase("a-a b-b", wordsep = c->c==' ')
"A-a B-b"
```
