```
ftranspose!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}, f::Function) where {Tv,Ti}
```

행렬 `A`를 전치하고 비영(非零) 요소에 함수 `f`를 적용하여 결과를 `X`에 저장합니다. `f`에 의해 생성된 영(零) 요소는 제거되지 않습니다. `size(X)`는 `size(transpose(A))`와 같아야 합니다. 필요할 경우 `X`의 rowval 및 nzval 크기를 조정하는 것 외에는 추가 메모리가 할당되지 않습니다.

`halfperm!`를 참조하세요.
