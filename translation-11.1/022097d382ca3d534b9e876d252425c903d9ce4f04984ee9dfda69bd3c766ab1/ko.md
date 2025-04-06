```
reim(A::AbstractArray)
```

`A`의 각 항목의 실수 부분과 허수 부분을 각각 포함하는 두 개의 배열로 이루어진 튜플을 반환합니다.

`(real.(A), imag.(A))`와 동등하지만, `eltype(A) <: Real`인 경우 `A`는 복사하지 않고 실수 부분을 나타내며, `A`가 0차원일 경우 스칼라 대신 0차원 배열이 반환됩니다.

# 예제

```jldoctest
julia> reim([1, 2im, 3 + 4im])
([1, 0, 3], [0, 2, 4])

julia> reim(fill(2 - im))
(fill(2), fill(-1))
```
