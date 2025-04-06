```
@view A[inds...]
```

인덱싱 표현식 `A[inds...]`를 동등한 [`view`](@ref) 호출로 변환합니다.

이는 단일 인덱싱 표현식에만 직접 적용할 수 있으며, `A[begin, 2:end-1]`와 같은 특별한 `begin` 또는 `end` 인덱싱 구문을 포함하는 표현식에 특히 유용합니다(이는 일반 [`view`](@ref) 함수에서 지원되지 않음).

`@view`는 일반 할당의 대상이 될 수 없으며(예: `@view(A[1, 2:end]) = ...`), 장식이 없는 [인덱스 할당](@ref man-indexed-assignment) (`A[1, 2:end] = ...`) 또는 브로드캐스트된 인덱스 할당 (`A[1, 2:end] .= ...`)도 복사본을 만들지 않습니다. 그러나 `@view(A[1, 2:end]) .+= 1`과 같은 브로드캐스트된 할당을 *업데이트*하는 데 유용할 수 있습니다. 이는 `@view(A[1, 2:end]) .= @view(A[1, 2:end]) + 1`에 대한 간단한 구문이며, 오른쪽의 인덱싱 표현식은 `@view` 없이 복사본을 만들 것입니다.

비스칼라 인덱싱에 대해 뷰를 사용하도록 전체 코드 블록을 전환하려면 [`@views`](@ref)도 참조하십시오.

!!! compat "Julia 1.5"
    인덱싱 표현식에서 첫 번째 인덱스를 참조하기 위해 `begin`을 사용하는 것은 최소한 Julia 1.5가 필요합니다.


# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = @view A[:, 1]
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3

julia> fill!(b, 0)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 0
 0

julia> A
2×2 Matrix{Int64}:
 0  2
 0  4
```
