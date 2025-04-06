```
sparse!(I::AbstractVector{Ti}, J::AbstractVector{Ti}, V::AbstractVector{Tv},
        m::Integer, n::Integer, combine, klasttouch::Vector{Ti},
        csrrowptr::Vector{Ti}, csrcolval::Vector{Ti}, csrnzval::Vector{Tv},
        [csccolptr::Vector{Ti}], [cscrowval::Vector{Ti}, cscnzval::Vector{Tv}] ) where {Tv,Ti<:Integer}
```

[`sparse`](@ref)의 부모 및 전문가 드라이버; 기본 사용법은 [`sparse`](@ref)를 참조하십시오. 이 메서드는 사용자가 아래에 설명된 대로 `sparse`의 중간 객체와 결과를 위한 미리 할당된 저장소를 제공할 수 있도록 합니다. 이 기능은 좌표 표현에서 [`SparseMatrixCSC`](@ref)로의 보다 효율적인 연속 구성을 가능하게 하며, 추가 비용 없이 결과의 전치의 정렬되지 않은 열 표현을 추출할 수 있게 합니다.

이 메서드는 세 가지 주요 단계로 구성됩니다: (1) 제공된 좌표 표현을 반복 항목을 포함한 정렬되지 않은 행 CSR 형식으로 카운팅 정렬합니다. (2) CSR 형식을 통해 스윕하면서 원하는 CSC 형식의 열 포인터 배열을 동시에 계산하고, 반복 항목을 감지하며, 반복 항목이 결합된 CSR 형식을 다시 포장합니다. 이 단계는 반복 항목이 없는 정렬되지 않은 행 CSR 형식을 생성합니다. (3) 이전 CSR 형식을 반복 항목이 없는 완전히 정렬된 CSC 형식으로 카운팅 정렬합니다.

입력 배열 `csrrowptr`, `csrcolval`, 및 `csrnzval`은 중간 CSR 형식의 저장소를 구성하며 `length(csrrowptr) >= m + 1`, `length(csrcolval) >= length(I)`, 및 `length(csrnzval >= length(I))`를 요구합니다. 입력 배열 `klasttouch`, 두 번째 단계의 작업 공간,은 `length(klasttouch) >= n`을 요구합니다. 선택적 입력 배열 `csccolptr`, `cscrowval`, 및 `cscnzval`은 반환된 CSC 형식 `S`의 저장소를 구성합니다. 필요할 경우, 이들은 `length(csccolptr) = n + 1`, `length(cscrowval) = nnz(S)` 및 `length(cscnzval) = nnz(S)`를 만족하도록 자동으로 크기가 조정됩니다. 따라서 `nnz(S)`가 처음에 알려지지 않은 경우, 적절한 유형의 빈 벡터(`Vector{Ti}()` 및 `Vector{Tv}()`)를 전달하거나 `cscrowval` 및 `cscnzval`을 무시하고 `sparse!` 메서드를 호출하면 충분합니다.

반환 시, `csrrowptr`, `csrcolval`, 및 `csrnzval`은 결과의 전치의 정렬되지 않은 열 표현을 포함합니다.

입력 배열의 저장소(`I`, `J`, `V`)를 출력 배열(`csccolptr`, `cscrowval`, `cscnzval`)에 재사용할 수 있습니다. 예를 들어, `sparse!(I, J, V, csrrowptr, csrcolval, csrnzval, I, J, V)`를 호출할 수 있습니다. 이들은 위의 조건을 만족하도록 크기가 조정됩니다.

효율성을 위해, 이 메서드는 `1 <= I[k] <= m` 및 `1 <= J[k] <= n`을 넘어서는 인수 검사를 수행하지 않습니다. 주의해서 사용하십시오. `--check-bounds=yes`로 테스트하는 것이 좋습니다.

이 메서드는 `O(m, n, length(I))` 시간에 실행됩니다. F. Gustavson의 "Two fast algorithms for sparse matrices: multiplication and permuted transposition," ACM TOMS 4(3), 250-269 (1978)에서 설명된 HALFPERM 알고리즘이 이 메서드의 카운팅 정렬 쌍 사용에 영감을 주었습니다.
