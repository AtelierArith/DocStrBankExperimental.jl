```
lu(A::AbstractSparseMatrixCSC; check = true, q = nothing, control = get_umfpack_control()) -> F::UmfpackLU
```

희소 행렬 `A`의 LU 분해를 계산합니다.

실수 또는 복소수 요소 유형을 가진 희소 `A`의 경우, `F`의 반환 유형은 `UmfpackLU{Tv, Ti}`이며, 여기서 `Tv`는 [`Float64`](@ref) 또는 `ComplexF64`이고, `Ti`는 정수 유형 ([`Int32`](@ref) 또는 [`Int64`](@ref))입니다.

`check = true`일 때, 분해가 실패하면 오류가 발생합니다. `check = false`일 때, 분해의 유효성을 확인하는 책임은 사용자에게 있습니다 (via [`issuccess`](@ref)).

치환 `q`는 치환 벡터이거나 `nothing`일 수 있습니다. 치환 벡터가 제공되지 않거나 `q`가 `nothing`인 경우, UMFPACK의 기본값이 사용됩니다. 치환이 0 기반이 아닐 경우, 0 기반 복사가 이루어집니다.

`control` 벡터는 UMFPACK에 대한 Julia SparseArrays 패키지의 기본 구성으로 기본값이 설정됩니다 (참고: 이는 반복 정제를 비활성화하기 위해 UMFPACK 기본값에서 수정됨), 그러나 `UMFPACK_CONTROL` 길이의 벡터를 전달하여 변경할 수 있습니다. 가능한 구성에 대해서는 UMFPACK 매뉴얼을 참조하십시오. 예를 들어 반복 정제를 다시 활성화하려면:

```
umfpack_control = SparseArrays.UMFPACK.get_umfpack_control(Float64, Int64) # Float64 희소 행렬에 대한 Julia 기본 구성 읽기
SparseArrays.UMFPACK.show_umf_ctrl(umfpack_control) # 선택 사항 - 값 표시
umfpack_control[SparseArrays.UMFPACK.JL_UMFPACK_IRSTEP] = 2.0 # 반복 정제 다시 활성화 (2는 UMFPACK 기본 최대 반복 정제 단계)

Alu = lu(A; control = umfpack_control)
x = Alu \ b   # Ax = b를 해결하며, UMFPACK 반복 정제를 포함
```

분해 `F`의 개별 구성 요소는 인덱싱하여 접근할 수 있습니다:

| 구성 요소 | 설명                   |
|:----- |:-------------------- |
| `L`   | `LU`의 `L` (하삼각) 부분   |
| `U`   | `LU`의 `U` (상삼각) 부분   |
| `p`   | 오른쪽 치환 `Vector`      |
| `q`   | 왼쪽 치환 `Vector`       |
| `Rs`  | 스케일링 계수의 `Vector`    |
| `:`   | `(L,U,p,q,Rs)` 구성 요소 |

`F`와 `A` 간의 관계는 다음과 같습니다.

`F.L*F.U == (F.Rs .* A)[F.p, F.q]`

`F`는 다음 함수를 추가로 지원합니다:

  * [`\`](@ref)
  * [`det`](@ref)

또한 [`lu!`](@ref)를 참조하십시오.

!!! note
    `lu(A::AbstractSparseMatrixCSC)`는 [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse)의 일부인 UMFPACK[^ACM832] 라이브러리를 사용합니다. 이 라이브러리는 [`Float64`](@ref) 또는 `ComplexF64` 요소를 가진 희소 행렬만 지원하므로, `lu`는 `A`를 적절하게 `SparseMatrixCSC{Float64}` 또는 `SparseMatrixCSC{ComplexF64}` 유형의 복사본으로 변환합니다.


[^ACM832]: Davis, Timothy A. (2004b). Algorithm 832: UMFPACK V4.3–-an Unsymmetric-Pattern Multifrontal Method. ACM Trans. Math. Softw., 30(2), 196–199. [doi:10.1145/992200.992206](https://doi.org/10.1145/992200.992206)
