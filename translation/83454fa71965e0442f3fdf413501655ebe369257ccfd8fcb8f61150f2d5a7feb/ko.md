```
norm(A, p::Real=2)
```

어떤 숫자의 반복 가능한 컨테이너 `A`(모든 차원의 배열 포함)에 대해 `p`-노름(`p=2`로 기본 설정됨)을 계산합니다. 이는 `A`가 해당 길이의 벡터인 것처럼 처리됩니다.

`p`-노름은 다음과 같이 정의됩니다.

$$
\|A\|_p = \left( \sum_{i=1}^n | a_i | ^p \right)^{1/p}
$$

여기서 $a_i$는 `A`의 항목, $| a_i |$는 [`norm`](@ref) $a_i$의 노름, $n$은 `A`의 길이입니다. `p`-노름은 `A`의 항목의 [`norm`](@ref)을 사용하여 계산되므로, `p != 2`인 경우 벡터의 벡터로서의 해석과 호환되지 않습니다.

`p`는 어떤 숫자 값도 가질 수 있습니다(모든 값이 수학적으로 유효한 벡터 노름을 생성하는 것은 아닙니다). 특히, `norm(A, Inf)`는 `abs.(A)`에서 가장 큰 값을 반환하고, `norm(A, -Inf)`는 가장 작은 값을 반환합니다. 만약 `A`가 행렬이고 `p=2`라면, 이는 프로베니우스 노름과 동등합니다.

두 번째 인수 `p`는 반드시 `norm`의 인터페이스의 일부가 아닙니다. 즉, 사용자 정의 유형은 두 번째 인수 없이 `norm(A)`만 구현할 수 있습니다.

행렬의 연산자 노름을 계산하려면 [`opnorm`](@ref)를 사용하십시오.

# 예제

```jldoctest
julia> v = [3, -2, 6]
3-element Vector{Int64}:
  3
 -2
  6

julia> norm(v)
7.0

julia> norm(v, 1)
11.0

julia> norm(v, Inf)
6.0

julia> norm([1 2 3; 4 5 6; 7 8 9])
16.881943016134134

julia> norm([1 2 3 4 5 6 7 8 9])
16.881943016134134

julia> norm(1:9)
16.881943016134134

julia> norm(hcat(v,v), 1) == norm(vcat(v,v), 1) != norm([v,v], 1)
true

julia> norm(hcat(v,v), 2) == norm(vcat(v,v), 2) == norm([v,v], 2)
true

julia> norm(hcat(v,v), Inf) == norm(vcat(v,v), Inf) != norm([v,v], Inf)
true
```
