```
asum(n, X, incx)
```

배열 `X`의 첫 번째 `n` 요소의 크기의 합을 stride `incx`로 계산합니다.

실수 배열의 경우, 크기는 절대값입니다. 복소수 배열의 경우, 크기는 실수 부분의 절대값과 허수 부분의 절대값의 합입니다.

# 예제

```jldoctest
julia> BLAS.asum(5, fill(1.0im, 10), 2)
5.0

julia> BLAS.asum(2, fill(1.0im, 10), 5)
2.0
```
