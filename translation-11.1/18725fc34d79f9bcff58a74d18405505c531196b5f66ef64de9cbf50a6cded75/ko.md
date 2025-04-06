```
view(A, inds...)
```

[`getindex`](@ref)와 유사하지만, 주어진 인덱스 또는 인덱스 집합 `inds`에서 부모 배열 `A`를 지연 참조(또는 사실상 *view*로)하는 경량 배열을 반환하며, 요소를 즉시 추출하거나 복사된 하위 집합을 구성하는 대신에 반환합니다. 반환된 값(종종 [`SubArray`](@ref))에서 [`getindex`](@ref) 또는 [`setindex!`](@ref)를 호출하면 부모 배열에 접근하거나 수정하기 위한 인덱스가 즉석에서 계산됩니다. `view`가 호출된 후 부모 배열의 형태가 변경되면 동작이 정의되지 않으며, 부모 배열에 대한 경계 검사가 없기 때문에 세그멘테이션 오류를 일으킬 수 있습니다.

일부 불변 부모 배열(예: 범위)은 효율적이고 호환 가능한 의미를 제공하는 경우 `SubArray`를 반환하는 대신 새로운 배열을 재계산하기로 선택할 수 있습니다.

!!! compat "Julia 1.6"
    Julia 1.6 이상에서는 `view`를 `AbstractString`에 호출할 수 있으며, `SubString`을 반환합니다.


# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = view(A, :, 1)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3

julia> fill!(b, 0)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 0
 0

julia> A # b를 수정했음에도 A가 변경되었음을 주목하세요
2×2 Matrix{Int64}:
 0  2
 0  4

julia> view(2:5, 2:3) # 타입이 불변이므로 범위를 반환합니다
3:4
```
