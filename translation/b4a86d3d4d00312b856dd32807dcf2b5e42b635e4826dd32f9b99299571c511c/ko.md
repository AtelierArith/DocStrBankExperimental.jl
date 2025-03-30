```
hessenberg(A) -> Hessenberg
```

행렬 `A`의 헤센베르크 분해를 계산하고 `Hessenberg` 객체를 반환합니다. 만약 `F`가 분해 객체라면, 유니타리 행렬은 `F.Q` (타입 `LinearAlgebra.HessenbergQ`)로 접근할 수 있으며, 헤센베르크 행렬은 `F.H` (타입 [`UpperHessenberg`](@ref))로 접근할 수 있습니다. 이 두 행렬은 각각 `Matrix(F.H)` 또는 `Matrix(F.Q)`를 사용하여 일반 행렬로 변환할 수 있습니다.

만약 `A`가 [`Hermitian`](@ref) 또는 실수-[`Symmetric`](@ref)이라면, 헤센베르크 분해는 실수-대칭 삼대각 행렬을 생성하며 `F.H`는 타입 [`SymTridiagonal`](@ref)입니다.

변형된 분해 `A+μI = Q (H+μI) Q'`는 [`UniformScaling`](@ref) 객체 [`I`](@ref)를 사용하여 `F + μ*I`로 효율적으로 구성할 수 있으며, 이는 공유 저장소와 수정된 이동을 가진 새로운 `Hessenberg` 객체를 생성합니다. 주어진 `F`의 이동은 `F.μ`로 얻을 수 있습니다. 이는 여러 개의 이동된 해를 `(F + μ*I) \ b` (다른 `μ` 및/또는 `b`에 대해) 효율적으로 수행할 수 있기 때문에 유용합니다. `F`가 생성된 후에 가능합니다.

분해를 반복하면 인수 `F.Q, F.H, F.μ`를 생성합니다.

# 예제

```julia-repl
julia> A = [4. 9. 7.; 4. 4. 1.; 4. 3. 2.]
3×3 Matrix{Float64}:
 4.0  9.0  7.0
 4.0  4.0  1.0
 4.0  3.0  2.0

julia> F = hessenberg(A)
Hessenberg{Float64, UpperHessenberg{Float64, Matrix{Float64}}, Matrix{Float64}, Vector{Float64}, Bool}
Q factor: 3×3 LinearAlgebra.HessenbergQ{Float64, Matrix{Float64}, Vector{Float64}, false}
H factor:
3×3 UpperHessenberg{Float64, Matrix{Float64}}:
  4.0      -11.3137       -1.41421
 -5.65685    5.0           2.0
   ⋅        -8.88178e-16   1.0

julia> F.Q * F.H * F.Q'
3×3 Matrix{Float64}:
 4.0  9.0  7.0
 4.0  4.0  1.0
 4.0  3.0  2.0

julia> q, h = F; # 반복을 통한 구조 분해

julia> q == F.Q && h == F.H
true
```
