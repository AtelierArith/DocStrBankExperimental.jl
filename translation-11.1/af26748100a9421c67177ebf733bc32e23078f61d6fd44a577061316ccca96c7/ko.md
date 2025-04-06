```
getindex(type[, elements...])
```

지정된 유형의 1차원 배열을 생성합니다. 이는 일반적으로 `Type[]` 구문으로 호출됩니다. 요소 값은 `Type[a,b,c,...]`를 사용하여 지정할 수 있습니다.

# 예제

```jldoctest
julia> Int8[1, 2, 3]
3-element Vector{Int8}:
 1
 2
 3

julia> getindex(Int8, 1, 2, 3)
3-element Vector{Int8}:
 1
 2
 3
```
