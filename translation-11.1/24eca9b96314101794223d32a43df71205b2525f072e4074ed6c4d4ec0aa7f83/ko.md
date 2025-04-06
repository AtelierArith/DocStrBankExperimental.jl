```
scal(n, a, X, incx)
scal(a, X)
```

`X`를 `a`로 스케일링하여 배열 `X`의 처음 `n` 요소를 `incx`의 보폭으로 반환합니다.

`n`과 `incx`가 제공되지 않으면 `length(X)`와 `stride(X,1)`이 사용됩니다.
