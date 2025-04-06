```
orgqr!(A, tau, k = length(tau))
```

`geqrf!`를 호출한 후 `QR` 분해의 행렬 `Q`를 명시적으로 찾습니다. `geqrf!`의 출력을 사용합니다. `A`는 `Q`로 덮어씌워집니다.
