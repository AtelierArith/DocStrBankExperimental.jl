```
rand([rng=default_rng()], [S], [dims...])
```

`S`로 지정된 값 집합에서 무작위 요소 또는 무작위 요소 배열을 선택합니다. `S`는 다음과 같을 수 있습니다.

  * 인덱스 가능한 컬렉션(예: `1:9` 또는 `('x', "y", :z)`)
  * `AbstractDict` 또는 `AbstractSet` 객체
  * 문자열(문자 집합으로 간주됨), 또는
  * 지정된 값 집합에 해당하는 아래 목록의 유형

      * 구체적인 정수 유형은 `typemin(S):typemax(S)`에서 샘플링합니다(지원되지 않는 [`BigInt`](@ref) 제외).
      * 구체적인 부동 소수점 유형은 `[0, 1)`에서 샘플링합니다.
      * 구체적인 복소수 유형 `Complex{T}`는 `T`가 샘플링 가능한 유형인 경우, `T`에 해당하는 값 집합에서 실수 및 허수 성분을 독립적으로 가져오지만, `T`가 샘플링 불가능한 경우 지원되지 않습니다.
      * 모든 `<:AbstractChar` 유형은 유효한 유니코드 스칼라 집합에서 샘플링합니다.
      * 사용자 정의 유형 및 값 집합; 구현 지침은 [Random API에 연결하기](@ref rand-api-hook)를 참조하십시오.
      * 알려진 크기의 튜플 유형이며 `S`의 각 매개변수가 샘플링 가능한 유형인 경우; `S` 유형의 값을 반환합니다. `Tuple{Vararg{T}}`(크기가 불명확한 튜플 유형) 및 `Tuple{1:2}`(값으로 매개변수화된 튜플 유형)는 지원되지 않습니다.
      * `Pair` 유형, 예: `Pair{X, Y}`로 `rand`가 `X` 및 `Y`에 대해 정의된 경우, 무작위 쌍이 생성됩니다.

`S`의 기본값은 [`Float64`](@ref)입니다. 선택적 `rng` 외에 하나의 인수만 전달되고 `Tuple`인 경우, 값 집합(`S`)의 컬렉션으로 해석되며 `dims`로 해석되지 않습니다.

정규 분포 숫자에 대해서는 [`randn`](@ref)를, 제자리에서의 동등한 함수에 대해서는 [`rand!`](@ref) 및 [`randn!`](@ref)를 참조하십시오.

!!! compat "Julia 1.1"
    `S`를 튜플로 지원하려면 최소한 Julia 1.1이 필요합니다.


!!! compat "Julia 1.11"
    `S`를 `Tuple` 유형으로 지원하려면 최소한 Julia 1.11이 필요합니다.


# 예제

```julia-repl
julia> rand(Int, 2)
2-element Array{Int64,1}:
 1339893410598768192
 1575814717733606317

julia> using Random

julia> rand(Xoshiro(0), Dict(1=>2, 3=>4))
3 => 4

julia> rand((2, 3))
3

julia> rand(Float64, (2, 3))
2×3 Array{Float64,2}:
 0.999717  0.0143835  0.540787
 0.696556  0.783855   0.938235
```

!!! note
    `rand(rng, s::Union{AbstractDict,AbstractSet})`의 복잡도는 `s`의 길이에 대해 선형이며, 상수 복잡도의 최적화된 방법이 사용 가능한 경우(예: `Dict`, `Set` 및 밀집 `BitSet`의 경우)입니다. 몇 번 이상의 호출을 위해서는 대신 `rand(rng, collect(s))`를 사용하거나 적절하게 `rand(rng, Dict(s))` 또는 `rand(rng, Set(s))`를 사용하십시오.

