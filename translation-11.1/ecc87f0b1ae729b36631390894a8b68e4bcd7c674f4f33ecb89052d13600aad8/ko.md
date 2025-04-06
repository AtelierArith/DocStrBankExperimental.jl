```
SparseArrays.sparse!(I, J, V, [m, n, combine]) -> SparseMatrixCSC
```

입력 벡터(`I`, `J`, `V`)를 최종 행렬 저장소에 재사용하는 `sparse!`의 변형입니다. 생성 후 입력 벡터는 행렬 버퍼를 참조하게 되며, `S.colptr === I`, `S.rowval === J`, `S.nzval === V`가 성립하며, 필요에 따라 `resize!`됩니다.

일부 작업 버퍼는 여전히 할당됩니다. 구체적으로, 이 메서드는 `sparse!(I, J, V, m, n, combine, klasttouch, csrrowptr, csrcolval, csrnzval, csccolptr, cscrowval, cscnzval)`에 대한 편의 래퍼로, 이 메서드는 적절한 크기의 `klasttouch`, `csrrowptr`, `csrcolval`, 및 `csrnzval`을 할당하지만, `csccolptr`, `cscrowval`, 및 `cscnzval`에 대해 `I`, `J`, 및 `V`를 재사용합니다.

인수 `m`, `n`, 및 `combine`의 기본값은 각각 `maximum(I)`, `maximum(J)`, 및 `+`입니다.

!!! compat "Julia 1.10"
    이 메서드는 Julia 버전 1.10 이상이 필요합니다.

