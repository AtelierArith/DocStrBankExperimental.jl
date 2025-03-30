```
setindex!(A, X, inds...)
A[inds...] = X
```

배열 `X`의 값을 `inds`로 지정된 `A`의 일부 하위 집합에 저장합니다. 구문 `A[inds...] = X`는 `(setindex!(A, X, inds...); X)`와 동일합니다.

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 때 동작이 예기치 않게 될 수 있습니다.

# 예제

```jldoctest
julia> A = zeros(2,2);

julia> setindex!(A, [10, 20], [1, 2]);

julia> A[[3, 4]] = [30, 40];

julia> A
2×2 Matrix{Float64}:
 10.0  30.0
 20.0  40.0
```
