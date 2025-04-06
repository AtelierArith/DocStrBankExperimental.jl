```
adjoint!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}) where {Tv,Ti}
```

행렬 `A`의 전치 행렬을 변환하고 행렬 `X`의 요소의 어드조인트를 저장합니다. `size(X)`는 `size(transpose(A))`와 같아야 합니다. 필요할 경우 `X`의 rowval 및 nzval을 크기 조정하는 것 외에는 추가 메모리가 할당되지 않습니다.

`halfperm!`을 참조하세요.
