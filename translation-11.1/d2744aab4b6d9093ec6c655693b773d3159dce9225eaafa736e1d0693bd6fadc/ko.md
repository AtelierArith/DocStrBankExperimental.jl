```
keepat!(a::Vector, inds)
keepat!(a::BitVector, inds)
```

주어진 `inds`에 의해 제공되지 않은 모든 인덱스의 항목을 제거하고 수정된 `a`를 반환합니다. 유지된 항목은 결과적으로 생긴 간격을 채우기 위해 이동됩니다.

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 경우 동작이 예기치 않게 나타날 수 있습니다.

`inds`는 정렬되고 고유한 정수 인덱스의 반복자여야 합니다. [`deleteat!`](@ref)도 참조하십시오.

!!! 호환성 "Julia 1.7"     이 함수는 Julia 1.7부터 사용할 수 있습니다.

# 예제

```jldoctest
julia> keepat!([6, 5, 4, 3, 2, 1], 1:2:5)
3-element Vector{Int64}:
 6
 4
 2
```
