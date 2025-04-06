```
pushfirst!(collection, items...) -> collection
```

`collection`의 시작 부분에 하나 이상의 `items`를 삽입합니다.

이 함수는 많은 다른 프로그래밍 언어에서 `unshift`라고 불립니다.

# 예제

```jldoctest
julia> pushfirst!([1, 2, 3, 4], 5, 6)
6-element Vector{Int64}:
 5
 6
 1
 2
 3
 4
```
