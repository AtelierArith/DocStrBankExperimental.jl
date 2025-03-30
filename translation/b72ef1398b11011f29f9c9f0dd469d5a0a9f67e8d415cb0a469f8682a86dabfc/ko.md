```
dot(n, X, incx, Y, incy)
```

두 벡터의 내적, 배열 `X`의 `n` 요소와 보폭 `incx`, 배열 `Y`의 `n` 요소와 보폭 `incy`로 구성됩니다.

# 예제

```jldoctest
julia> BLAS.dot(10, fill(1.0, 10), 1, fill(1.0, 20), 2)
10.0
```
