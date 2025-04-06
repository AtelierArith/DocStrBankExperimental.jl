```
issorted(v, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

컬렉션이 정렬된 순서인지 테스트합니다. 키워드는 [`sort!`](@ref) 문서에 설명된 대로 어떤 순서가 정렬된 것으로 간주되는지를 수정합니다.

# 예제

```jldoctest
julia> issorted([1, 2, 3])
true

julia> issorted([(1, "b"), (2, "a")], by = x -> x[1])
true

julia> issorted([(1, "b"), (2, "a")], by = x -> x[2])
false

julia> issorted([(1, "b"), (2, "a")], by = x -> x[2], rev=true)
true

julia> issorted([1, 2, -2, 3], by=abs)
true
```
