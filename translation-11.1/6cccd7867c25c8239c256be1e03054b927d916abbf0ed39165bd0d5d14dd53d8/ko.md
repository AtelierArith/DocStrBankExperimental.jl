```
spzeros([type], I::AbstractVector, J::AbstractVector, [m, n])
```

구조적 제로가 있는 차원 `m x n`의 희소 행렬 `S`를 생성합니다. `S[I[k], J[k]]`에 구조적 제로가 있습니다.

이 방법은 행렬의 희소성 패턴을 구성하는 데 사용될 수 있으며, 예를 들어 `sparse(I, J, zeros(length(I)))`를 사용하는 것보다 더 효율적입니다.

추가 문서 및 전문가 드라이버에 대한 내용은 `SparseArrays.spzeros!`를 참조하십시오.

!!! compat "Julia 1.10"
    이 방법은 Julia 버전 1.10 이상이 필요합니다.

