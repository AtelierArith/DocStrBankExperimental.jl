```
deleteat!(a::Vector, inds)
```

주어진 `inds`에 의해 인덱스에서 항목을 제거하고 수정된 `a`를 반환합니다. 이후 항목들은 결과적으로 생긴 간격을 채우기 위해 이동됩니다.

`inds`는 반복자이거나 정렬되고 고유한 정수 인덱스의 컬렉션, 또는 `a`와 동일한 길이의 부울 벡터일 수 있으며, `true`는 삭제할 항목을 나타냅니다.

# 예제

```jldoctest
julia> deleteat!([6, 5, 4, 3, 2, 1], 1:2:5)
3-element Vector{Int64}:
 5
 3
 1

julia> deleteat!([6, 5, 4, 3, 2, 1], [true, false, true, false, true, false])
3-element Vector{Int64}:
 5
 3
 1

julia> deleteat!([6, 5, 4, 3, 2, 1], (2, 2))
ERROR: ArgumentError: indices must be unique and sorted
Stacktrace:
[...]
```
