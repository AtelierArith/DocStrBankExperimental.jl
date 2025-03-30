```
transpose!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}) where {Tv,Ti}
```

행렬 `A`를 전치하여 행렬 `X`에 저장합니다. `size(X)`는 `size(transpose(A))`와 같아야 합니다. 필요할 경우 `X`의 rowval 및 nzval 크기를 조정하는 것 외에는 추가 메모리가 할당되지 않습니다.

`halfperm!`를 참조하세요.
