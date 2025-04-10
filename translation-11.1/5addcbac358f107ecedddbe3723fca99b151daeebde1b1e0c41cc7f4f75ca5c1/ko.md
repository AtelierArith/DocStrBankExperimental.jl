```
spr!(uplo, α, x, AP)
```

행렬 `A`를 `A+α*x*x'`로 업데이트합니다. 여기서 `A`는 패킹 형식 `AP`로 제공되는 대칭 행렬이고, `x`는 벡터입니다.

`uplo = 'U'`인 경우, 배열 AP는 대칭 행렬의 상삼각 부분을 열 단위로 순차적으로 포함해야 하며, 따라서 `AP[1]`은 `A[1, 1]`을 포함하고, `AP[2]`와 `AP[3]`는 각각 `A[1, 2]`와 `A[2, 2]`를 포함해야 합니다. 계속해서 이와 같은 방식으로 진행됩니다.

`uplo = 'L'`인 경우, 배열 AP는 대칭 행렬의 하삼각 부분을 열 단위로 순차적으로 포함해야 하며, 따라서 `AP[1]`은 `A[1, 1]`을 포함하고, `AP[2]`와 `AP[3]`는 각각 `A[2, 1]`과 `A[3, 1]`을 포함해야 합니다. 계속해서 이와 같은 방식으로 진행됩니다.

스칼라 입력 `α`는 실수여야 합니다.

배열 입력 `x`와 `AP`는 모두 `Float32` 또는 `Float64` 유형이어야 합니다. 업데이트된 `AP`를 반환합니다.

!!! compat "Julia 1.8"
    `spr!`는 최소한 Julia 1.8이 필요합니다.

