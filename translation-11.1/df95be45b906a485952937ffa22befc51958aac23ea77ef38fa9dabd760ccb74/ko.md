```
dotu(n, X, incx, Y, incy)
```

두 개의 복소수 벡터에 대한 Dot 함수로, 배열 `X`의 `n` 요소와 보폭 `incx`, 배열 `Y`의 `n` 요소와 보폭 `incy`로 구성됩니다.

# 예제

```jldoctest
julia> BLAS.dotu(10, fill(1.0im, 10), 1, fill(1.0+im, 20), 2)
-10.0 + 10.0im
```
