```
opnorm(A::AbstractMatrix, p::Real=2)
```

벡터 `p`-노름에 의해 유도된 연산자 노름(또는 행렬 노름)을 계산합니다. 여기서 유효한 `p` 값은 `1`, `2`, 또는 `Inf`입니다. (희소 행렬의 경우, 현재 `p=2`는 구현되어 있지 않습니다.) 프로베니우스 노름을 계산하기 위해 [`norm`](@ref)를 사용하십시오.

`p=1`일 때, 연산자 노름은 `A`의 최대 절대 열 합계입니다:

$$
\|A\|_1 = \max_{1 ≤ j ≤ n} \sum_{i=1}^m | a_{ij} |
$$

여기서 $a_{ij}$는 $A$의 항목이며, $m$과 $n$은 그 차원입니다.

`p=2`일 때, 연산자 노름은 스펙트럴 노름으로, `A`의 가장 큰 특이값과 같습니다.

`p=Inf`일 때, 연산자 노름은 `A`의 최대 절대 행 합계입니다:

$$
\|A\|_\infty = \max_{1 ≤ i ≤ m} \sum _{j=1}^n | a_{ij} |
$$

# 예제

```jldoctest
julia> A = [1 -2 -3; 2 3 -1]
2×3 Matrix{Int64}:
 1  -2  -3
 2   3  -1

julia> opnorm(A, Inf)
6.0

julia> opnorm(A, 1)
5.0
```
