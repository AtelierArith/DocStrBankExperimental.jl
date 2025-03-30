```
SparseArrays.spzeros!(::Type{Tv}, I, J, [m, n]) -> SparseMatrixCSC{Tv}
```

입력 벡터 `I`와 `J`를 최종 행렬 저장소에 재사용하는 `spzeros!`의 변형입니다. 생성 후 입력 벡터는 행렬 버퍼를 별칭으로 사용하게 되며, `S.colptr === I` 및 `S.rowval === J`가 성립하고 필요에 따라 `resize!`됩니다.

일부 작업 버퍼는 여전히 할당될 것임에 유의하십시오. 구체적으로, 이 메서드는 `spzeros!(Tv, I, J, m, n, klasttouch, csrrowptr, csrcolval, csccolptr, cscrowval)`에 대한 편의 래퍼이며, 이 메서드는 적절한 크기의 `klasttouch`, `csrrowptr`, 및 `csrcolval`을 할당하지만 `csccolptr` 및 `cscrowval`에 대해 `I`와 `J`를 재사용합니다.

인수 `m`과 `n`은 각각 `maximum(I)` 및 `maximum(J)`로 기본값이 설정됩니다.

!!! compat "Julia 1.10"
    이 메서드는 Julia 버전 1.10 이상이 필요합니다.

