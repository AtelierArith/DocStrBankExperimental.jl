```
dotc(n, X, incx, U, incy)
```

두 개의 복소수 벡터에 대한 Dot 함수로, stride `incx`를 가진 배열 `X`의 `n` 요소와 stride `incy`를 가진 배열 `U`의 `n` 요소로 구성되며, 첫 번째 벡터를 켤레합니다.

# 예제

```jldoctest
julia> BLAS.dotc(10, fill(1.0im, 10), 1, fill(1.0+im, 20), 2)
10.0 - 10.0im
```
