```
fill(value, dims::Tuple)
fill(value, dims...)
```

모든 위치가 `value`로 설정된 크기 `dims`의 배열을 생성합니다.

예를 들어, `fill(1.0, (5,5))`는 배열의 모든 위치에 `1.0`이 있는 5×5 부동 소수점 배열을 반환합니다.

차원 길이 `dims`는 튜플 또는 인수 시퀀스로 지정할 수 있습니다. `N` 길이의 튜플 또는 `value` 다음에 오는 `N` 개의 인수는 `N` 차원 배열을 지정합니다. 따라서, 유일한 위치가 `x`로 설정된 0차원 배열을 생성하는 일반적인 관용구는 `fill(x)`입니다.

반환된 배열의 모든 위치는 전달된 `value`에 설정되어 있으며, 따라서 [`===`](@ref)와 같습니다. 이는 `value`가 수정되면 `fill`된 배열의 모든 요소가 그 수정 사항을 반영한다는 것을 의미합니다. 왜냐하면 그들은 여전히 그 `value`이기 때문입니다. `fill(1.0, (5,5))`의 경우 `value`인 `1.0`은 불변이므로 수정할 수 없지만, 배열과 같은 가변 값에서는 예상치 못한 결과를 초래할 수 있습니다. 예를 들어, `fill([], 3)`은 반환된 벡터의 세 위치에 *같은* 빈 배열을 배치합니다:

```jldoctest
julia> v = fill([], 3)
3-element Vector{Vector{Any}}:
 []
 []
 []

julia> v[1] === v[2] === v[3]
true

julia> value = v[1]
Any[]

julia> push!(value, 867_5309)
1-element Vector{Any}:
 8675309

julia> v
3-element Vector{Vector{Any}}:
 [8675309]
 [8675309]
 [8675309]
```

많은 독립적인 내부 배열을 생성하려면 대신 [comprehension](@ref man-comprehensions)을 사용하십시오. 이는 루프의 각 반복에서 새롭고 독립적인 배열을 생성합니다:

```jldoctest
julia> v2 = [[] for _ in 1:3]
3-element Vector{Vector{Any}}:
 []
 []
 []

julia> v2[1] === v2[2] === v2[3]
false

julia> push!(v2[1], 8675309)
1-element Vector{Any}:
 8675309

julia> v2
3-element Vector{Vector{Any}}:
 [8675309]
 []
 []
```

또한 참조하십시오: [`fill!`](@ref), [`zeros`](@ref), [`ones`](@ref), [`similar`](@ref).

# 예제

```jldoctest
julia> fill(1.0, (2,3))
2×3 Matrix{Float64}:
 1.0  1.0  1.0
 1.0  1.0  1.0

julia> fill(42)
0-dimensional Array{Int64, 0}:
42

julia> A = fill(zeros(2), 2) # 두 요소를 동일한 [0.0, 0.0] 벡터로 설정
2-element Vector{Vector{Float64}}:
 [0.0, 0.0]
 [0.0, 0.0]

julia> A[1][1] = 42; # 채워진 값을 [42.0, 0.0]으로 수정

julia> A # A[1]과 A[2]는 동일한 벡터입니다
2-element Vector{Vector{Float64}}:
 [42.0, 0.0]
 [42.0, 0.0]
```
