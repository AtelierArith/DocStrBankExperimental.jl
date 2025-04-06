```
cholesky(A, NoPivot(); check = true) -> Cholesky
```

밀집 대칭 양의 정부호 행렬 `A`의 Cholesky 분해를 계산하고 [`Cholesky`](@ref) 분해를 반환합니다. 행렬 `A`는 [`Symmetric`](@ref) 또는 [`Hermitian`](@ref) [`AbstractMatrix`](@ref)일 수 있으며, *완벽하게* 대칭 또는 에르미트 `AbstractMatrix`일 수 있습니다.

삼각형 Cholesky 인자는 분해 `F`에서 `F.L` 및 `F.U`를 통해 얻을 수 있으며, 여기서 `A ≈ F.U' * F.U ≈ F.L * F.L'`입니다.

`Cholesky` 객체에 대해 사용할 수 있는 함수는 [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), [`logdet`](@ref) 및 [`isposdef`](@ref)입니다.

구성 과정에서 반올림 오류로 인해 약간 비에르미트인 행렬 `A`가 있는 경우, `cholesky`에 전달하기 전에 `Hermitian(A)`로 감싸서 완벽한 에르미트로 처리하십시오.

`check = true`일 때 분해가 실패하면 오류가 발생합니다. `check = false`일 때 분해의 유효성을 확인하는 책임은 사용자에게 있습니다( [`issuccess`](@ref) 사용).

# 예제

```jldoctest
julia> A = [4. 12. -16.; 12. 37. -43.; -16. -43. 98.]
3×3 Matrix{Float64}:
   4.0   12.0  -16.0
  12.0   37.0  -43.0
 -16.0  -43.0   98.0

julia> C = cholesky(A)
Cholesky{Float64, Matrix{Float64}}
U 인자:
3×3 UpperTriangular{Float64, Matrix{Float64}}:
 2.0  6.0  -8.0
  ⋅   1.0   5.0
  ⋅    ⋅    3.0

julia> C.U
3×3 UpperTriangular{Float64, Matrix{Float64}}:
 2.0  6.0  -8.0
  ⋅   1.0   5.0
  ⋅    ⋅    3.0

julia> C.L
3×3 LowerTriangular{Float64, Matrix{Float64}}:
  2.0   ⋅    ⋅
  6.0  1.0   ⋅
 -8.0  5.0  3.0

julia> C.L * C.U == A
true
```
