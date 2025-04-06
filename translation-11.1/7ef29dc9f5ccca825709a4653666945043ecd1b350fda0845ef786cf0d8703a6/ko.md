```
scal!(n, a, X, incx)
scal!(a, X)
```

배열 `X`의 처음 `n` 요소를 `a*X`로 덮어씁니다. 보폭은 `incx`입니다. `X`를 반환합니다.

`n`과 `incx`가 제공되지 않으면 `length(X)`와 `stride(X,1)`이 사용됩니다.
