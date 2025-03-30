```
push!(collection, items...) -> collection
```

하나 이상의 `items`를 `collection`에 삽입합니다. `collection`이 정렬된 컨테이너인 경우, 항목은 끝에 삽입됩니다(주어진 순서로).

# 예제

```jldoctest
julia> push!([1, 2, 3], 4, 5, 6)
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

`collection`이 정렬된 경우, [`append!`](@ref)를 사용하여 다른 컬렉션의 모든 요소를 추가할 수 있습니다. 앞의 예의 결과는 `append!([1, 2, 3], [4, 5, 6])`와 동일합니다. `AbstractSet` 객체의 경우, 대신 [`union!`](@ref)를 사용할 수 있습니다.

성능 모델에 대한 참고 사항은 [`sizehint!`](@ref)를 참조하십시오.

또한 [`pushfirst!`](@ref)도 참조하십시오.
