```
collect(element_type, collection)
```

주어진 요소 유형의 모든 항목이 포함된 `Array`를 반환합니다. 결과는 `collection`과 동일한 형태와 차원 수를 가집니다.

# 예제

```jldoctest
julia> collect(Float64, 1:2:5)
3-element Vector{Float64}:
 1.0
 3.0
 5.0
```
