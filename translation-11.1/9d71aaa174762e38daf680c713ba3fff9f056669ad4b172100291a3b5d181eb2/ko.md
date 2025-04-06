```
lowrankdowndate(C::Cholesky, v::AbstractVector) -> CC::Cholesky
```

Cholesky 분해 `C`를 벡터 `v`로 다운데이트합니다. 만약 `A = C.U'C.U`라면 `CC = cholesky(C.U'C.U - v*v')`이지만, `CC`의 계산은 `O(n^2)` 연산만 사용합니다.
