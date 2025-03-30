```
randn([rng=default_rng()], [T=Float64], [dims...])
```

평균 0과 표준 편차 1을 가진 `T` 유형의 정규 분포 난수를 생성합니다. 선택적 `dims` 인수를 사용하여 이러한 숫자의 크기가 `dims`인 배열을 생성합니다. Julia의 표준 라이브러리는 [`rand`](@ref)를 구현하는 모든 부동 소수점 유형에 대해 `randn`을 지원합니다. 예를 들어, `Base` 유형인 [`Float16`](@ref), [`Float32`](@ref), [`Float64`](@ref) (기본값) 및 [`BigFloat`](@ref)와 그들의 [`Complex`](@ref) 대응형이 있습니다.

(`T`가 복소수일 때, 값은 분산 1의 원형 대칭 복소 정규 분포에서 추출되며, 이는 실수 및 허수 부분이 평균 0과 분산 `1/2`를 가진 독립적인 정규 분포를 갖는 것에 해당합니다).

제자리에서 작동하기 위해 [`randn!`](@ref)도 참조하십시오.

# 예제

단일 난수 생성 (기본 `Float64` 유형 사용):

```julia-repl
julia> randn()
-0.942481877315864
```

정규 난수 행렬 생성 (기본 `Float64` 유형 사용):

```julia-repl
julia> randn(2,3)
2×3 Matrix{Float64}:
  1.18786   -0.678616   1.49463
 -0.342792  -0.134299  -1.45005
```

사용자 정의 시드를 사용하여 난수 생성기 `rng`를 설정하고 이를 사용하여 난수 `Float32` 또는 `ComplexF32` 난수 행렬을 생성하는 예:

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> randn(rng, Float32)
-0.6457307f0

julia> randn(rng, ComplexF32, (2, 3))
2×3 Matrix{ComplexF32}:
  -1.03467-1.14806im  0.693657+0.056538im   0.291442+0.419454im
 -0.153912+0.34807im    1.0954-0.948661im  -0.543347-0.0538589im
```
