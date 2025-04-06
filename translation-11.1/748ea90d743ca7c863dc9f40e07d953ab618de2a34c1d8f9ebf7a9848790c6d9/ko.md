```
trexc!(compq, ifst, ilst, T, Q) -> (T, Q)
trexc!(ifst, ilst, T, Q) -> (T, Q)
```

행렬의 Schur 분해 `T`를 재정렬하여, 행 인덱스 `ifst`를 가진 `T`의 대각 블록이 행 인덱스 `ilst`로 이동하도록 합니다. `compq = V`인 경우, Schur 벡터 `Q`가 재정렬됩니다. `compq = N`인 경우, 수정되지 않습니다. 4-인자 메서드는 `compq = V`로 5-인자 메서드를 호출합니다.
