```
nrm2(n, X, incx)
```

`incx`의 보폭을 가진 배열 `X`의 `n` 요소로 구성된 벡터의 2-노름입니다.

# 예제

```jldoctest
julia> BLAS.nrm2(4, fill(1.0, 8), 2)
2.0

julia> BLAS.nrm2(1, fill(1.0, 8), 2)
1.0
```
