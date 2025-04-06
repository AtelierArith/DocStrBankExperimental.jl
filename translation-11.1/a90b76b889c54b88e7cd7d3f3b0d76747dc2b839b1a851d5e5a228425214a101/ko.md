```
peel(iter)
```

첫 번째 요소와 나머지 요소에 대한 반복자를 반환합니다.

반복자가 비어 있으면 `nothing`을 반환합니다 (예: `iterate`와 같음).

!!! compat "Julia 1.7"
    이전 버전에서는 반복자가 비어 있을 경우 BoundsError를 발생시킵니다.


참고: [`Iterators.drop`](@ref), [`Iterators.take`](@ref).

# 예제

```jldoctest
julia> (a, rest) = Iterators.peel("abc");

julia> a
'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)

julia> collect(rest)
2-element Vector{Char}:
 'b': ASCII/Unicode U+0062 (category Ll: Letter, lowercase)
 'c': ASCII/Unicode U+0063 (category Ll: Letter, lowercase)
```
