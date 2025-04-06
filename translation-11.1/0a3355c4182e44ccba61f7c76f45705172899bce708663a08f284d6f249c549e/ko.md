```
zip(iters...)
```

여러 이터레이터를 동시에 실행하며, 그 중 하나가 소진될 때까지 진행합니다. `zip` 이터레이터의 값 유형은 하위 이터레이터의 값 튜플입니다.

!!! note
    `zip`은 상태가 있는 이터레이터가 현재 반복에서 다른 이터레이터가 완료될 때 진행되지 않도록 하위 이터레이터에 대한 호출을 정렬합니다.


!!! note
    인수가 없는 `zip()`은 빈 튜플의 무한 이터레이터를 생성합니다.


참고: [`enumerate`](@ref), [`Base.splat`](@ref).

# 예제

```jldoctest
julia> a = 1:5
1:5

julia> b = ["e","d","b","c","a"]
5-element Vector{String}:
 "e"
 "d"
 "b"
 "c"
 "a"

julia> c = zip(a,b)
zip(1:5, ["e", "d", "b", "c", "a"])

julia> length(c)
5

julia> first(c)
(1, "e")
```
