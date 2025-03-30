```
trsyl!(transa, transb, A, B, C, isgn=1) -> (C, scale)
```

실베스터 행렬 방정식 `A * X +/- X * B = scale*C`를 해결합니다. 여기서 `A`와 `B`는 모두 준상삼각형입니다. `transa = N`인 경우, `A`는 수정되지 않습니다. `transa = T`인 경우, `A`는 전치됩니다. `transa = C`인 경우, `A`는 켤레 전치됩니다. `transb`와 `B`에 대해서도 마찬가지입니다. `isgn = 1`인 경우, 방정식 `A * X + X * B = scale * C`가 해결됩니다. `isgn = -1`인 경우, 방정식 `A * X - X * B = scale * C`가 해결됩니다.

`X`(C를 덮어씀)와 `scale`을 반환합니다.
