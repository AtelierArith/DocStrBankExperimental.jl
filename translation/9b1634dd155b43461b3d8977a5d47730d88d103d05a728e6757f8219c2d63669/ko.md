```
iamax(n, dx, incx)
iamax(dx)
```

`dx`의 최대 절대값을 가진 요소의 인덱스를 찾습니다. `n`은 `dx`의 길이이며, `incx`는 보폭입니다. `n`과 `incx`가 제공되지 않으면 기본값인 `n=length(dx)`와 `incx=stride1(dx)`를 가정합니다.
