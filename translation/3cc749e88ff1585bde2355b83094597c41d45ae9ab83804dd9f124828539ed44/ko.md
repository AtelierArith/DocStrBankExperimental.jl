```
Cholesky <: Factorization
```

밀집 대칭/에르미트 양의 정부호 행렬 `A`의 Cholesky 분해의 행렬 분해 유형입니다. 이는 해당 행렬 분해 함수인 [`cholesky`](@ref)의 반환 유형입니다.

삼각형 Cholesky 인자는 분해 `F::Cholesky`에서 `F.L` 및 `F.U`를 통해 얻을 수 있으며, 여기서 `A ≈ F.U' * F.U ≈ F.L * F.L'`입니다.

`Cholesky` 객체에 대해 사용할 수 있는 함수는 [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), [`logdet`](@ref) 및 [`isposdef`](@ref)입니다.

분해를 반복하면 구성 요소 `L`과 `U`가 생성됩니다.

# 예제

```jldoctest
julia> A = [4. 12. -16.; 12. 37. -43.; -16. -43. 98.]
3×3 Matrix{Float64}:
   4.0   12.0  -16.0
  12.0   37.0  -43.0
 -16.0  -43.0   98.0

julia> C = cholesky(A)
Cholesky{Float64, Matrix{Float64}}
U factor:
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

julia> l, u = C; # destructuring via iteration

julia> l == C.L && u == C.U
true
```
