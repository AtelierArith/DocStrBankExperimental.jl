```
append!(collection, collections...) -> collection.
```

정렬된 컨테이너 `collection`에 각 `collections`의 요소를 끝에 추가합니다.

!!! compat "Julia 1.6"
    여러 개의 컬렉션을 추가하려면 최소한 Julia 1.6이 필요합니다.


# 예제

```jldoctest
julia> append!([1], [2, 3])
3-element Vector{Int64}:
 1
 2
 3

julia> append!([1, 2, 3], [4, 5], [6])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

개별 항목을 `collection`에 추가하려면 [`push!`](@ref)를 사용하세요. 이 항목들은 다른 컬렉션에 이미 포함되어 있지 않아야 합니다. 앞선 예제의 결과는 `push!([1, 2, 3], 4, 5, 6)`와 동일합니다.

성능 모델에 대한 참고 사항은 [`sizehint!`](@ref)를 참조하세요.

벡터에 대해서는 [`vcat`](@ref), 집합에 대해서는 [`union!`](@ref), 반대 순서에 대해서는 [`prepend!`](@ref) 및 [`pushfirst!`](@ref)를 참조하세요.
