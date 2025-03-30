```
rank(A::AbstractMatrix; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
rank(A::AbstractMatrix, rtol::Real)
```

행렬의 수치적 랭크를 계산하여 `svdvals(A)`의 출력 중 `max(atol, rtol*σ₁)`보다 큰 값의 개수를 셉니다. 여기서 `σ₁`은 `A`의 가장 큰 계산된 특이값입니다. `atol`과 `rtol`은 각각 절대 및 상대 허용오차입니다. 기본 상대 허용오차는 `n*ϵ`이며, 여기서 `n`은 `A`의 가장 작은 차원의 크기이고, `ϵ`는 `A`의 요소 유형의 [`eps`](@ref)입니다.

!!! note
    수치적 랭크는 특이값이 임계 허용오차 `max(atol, rtol*σ₁)`에 가까운 잘못된 조건의 행렬에 대해 민감하고 부정확한 특성화가 될 수 있습니다. 이러한 경우, 특이값 계산이나 행렬에 대한 약간의 섭동이 하나 이상의 특이값을 임계값을 넘어 이동시켜 `rank`의 결과를 변경할 수 있습니다. 이러한 변동은 서로 다른 Julia 버전, 아키텍처, 컴파일러 또는 운영 체제 간의 부동 소수점 오류의 변화로 인해 발생할 수 있습니다.


!!! compat "Julia 1.1"
    `atol` 및 `rtol` 키워드 인자는 최소한 Julia 1.1이 필요합니다. Julia 1.0에서는 `rtol`이 위치 인자로 사용 가능하지만, 이는 Julia 2.0에서 더 이상 지원되지 않을 예정입니다.


# 예제

```jldoctest
julia> rank(Matrix(I, 3, 3))
3

julia> rank(diagm(0 => [1, 0, 2]))
2

julia> rank(diagm(0 => [1, 0.001, 2]), rtol=0.1)
2

julia> rank(diagm(0 => [1, 0.001, 2]), rtol=0.00001)
3

julia> rank(diagm(0 => [1, 0.001, 2]), atol=1.5)
1
```
