```
map(f, c...) -> collection
```

컬렉션 `c`의 각 요소에 `f`를 적용하여 변환합니다. 여러 개의 컬렉션 인수가 있는 경우, 요소별로 `f`를 적용하며, 그 중 하나라도 소진되면 중지합니다.

자세한 내용은 [`map!`](@ref), [`foreach`](@ref), [`mapreduce`](@ref), [`mapslices`](@ref), [`zip`](@ref), [`Iterators.map`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> map(x -> x * 2, [1, 2, 3])
3-element Vector{Int64}:
 2
 4
 6

julia> map(+, [1, 2, 3], [10, 20, 30, 400, 5000])
3-element Vector{Int64}:
 11
 22
 33
```
