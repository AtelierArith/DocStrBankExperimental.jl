```
rot!(n, X, incx, Y, incy, c, s)
```

`X`를 `c*X + s*Y`로 덮어쓰고 `Y`를 `-conj(s)*X + c*Y`로 덮어씁니다. 배열 `X`의 첫 `n` 요소와 보폭 `incx`를 사용하고 배열 `Y`의 첫 `n` 요소와 보폭 `incy`를 사용합니다. `X`와 `Y`를 반환합니다.

!!! compat "Julia 1.5"
    `rot!`는 최소한 Julia 1.5가 필요합니다.

