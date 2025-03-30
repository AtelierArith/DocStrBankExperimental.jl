```
axes(A, d)
```

배열 `A`의 차원 `d`에 대한 유효한 인덱스 범위를 반환합니다.

또한 [`size`](@ref) 및 [사용자 정의 인덱스를 가진 배열](@ref man-custom-indices)에 대한 매뉴얼 장을 참조하십시오.

# 예제

```jldoctest
julia> A = fill(1, (5,6,7));

julia> axes(A, 2)
Base.OneTo(6)

julia> axes(A, 4) == 1:1  # 모든 차원 d > ndims(A)는 크기가 1입니다.
true
```

# 사용 주의사항

각 인덱스는 `AbstractUnitRange{<:Integer}` 여야 하지만, 동시에 사용자 정의 인덱스를 사용하는 타입일 수도 있습니다. 예를 들어, 하위 집합이 필요하다면 `begin`/`end` 또는 [`firstindex`](@ref)/[`lastindex`](@ref)와 같은 일반화된 인덱싱 구조를 사용하십시오:

```julia
ix = axes(v, 1)
ix[2:end]          # 예를 들어 Vector에 대해 작동하지만 일반적으로 실패할 수 있습니다.
ix[(begin+1):end]  # 일반화된 인덱스에 대해 작동합니다.
```
