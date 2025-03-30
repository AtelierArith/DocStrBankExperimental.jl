```
graphemes(s::AbstractString, m:n) -> SubString
```

`s`의 `m`-번째부터 `n`-번째 그래프의 [`SubString`](@ref)을 반환합니다. 여기서 두 번째 인수 `m:n`은 정수 값의 [`AbstractUnitRange`](@ref)입니다.

느슨하게 말하자면, 이는 문자열에서 `m:n`-번째 사용자 인식 "문자"에 해당합니다. 예를 들어:

```jldoctest
julia> s = graphemes("exposé", 3:6)
"posé"

julia> collect(s)
5-element Vector{Char}:
 'p': ASCII/Unicode U+0070 (category Ll: Letter, lowercase)
 'o': ASCII/Unicode U+006F (category Ll: Letter, lowercase)
 's': ASCII/Unicode U+0073 (category Ll: Letter, lowercase)
 'e': ASCII/Unicode U+0065 (category Ll: Letter, lowercase)
 '́': Unicode U+0301 (category Mn: Mark, nonspacing)
```

이는 `"exposé"`에서 3번째부터 *7번째* 코드포인트([`Char`](@ref)s)로 구성됩니다. 왜냐하면 그래프 `"é"`는 실제로 *두 개*의 유니코드 코드포인트(문자 `'e'`와 그 뒤에 오는 발음 기호 결합 문자 U+0301)로 이루어져 있기 때문입니다.

그래프 경계를 찾기 위해 문자열 내용을 반복해야 하므로, `graphemes(s, m:n)` 함수는 서브스트링의 끝 이전에 문자열의 길이(코드포인트 수)에 비례하는 시간이 필요합니다.

!!! compat "Julia 1.9"
    `graphemes`의 `m:n` 인수는 Julia 1.9가 필요합니다.


```
