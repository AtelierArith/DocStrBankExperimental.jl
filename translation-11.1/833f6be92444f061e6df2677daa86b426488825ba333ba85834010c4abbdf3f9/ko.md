# Bounds checking

많은 현대 프로그래밍 언어와 마찬가지로, Julia는 배열에 접근할 때 프로그램의 안전성을 보장하기 위해 경계 검사를 사용합니다. 타이트한 내부 루프나 다른 성능이 중요한 상황에서는 이러한 경계 검사를 건너뛰어 실행 성능을 향상시키고 싶을 수 있습니다. 예를 들어, 벡터화된(SIMD) 명령어를 생성하기 위해서는 루프 본문에 분기가 포함될 수 없으므로 경계 검사를 포함할 수 없습니다. 따라서 Julia는 주어진 블록 내에서 이러한 경계 검사를 건너뛰도록 컴파일러에 지시하는 `@inbounds(...)` 매크로를 포함합니다. 사용자 정의 배열 유형은 `@boundscheck(...)` 매크로를 사용하여 문맥에 민감한 코드 선택을 달성할 수 있습니다.

## Eliding bounds checks

`@boundscheck(...)` 매크로는 경계 검사를 수행하는 코드 블록을 표시합니다. 이러한 블록이 `@inbounds(...)` 블록에 인라인될 때, 컴파일러는 이러한 블록을 제거할 수 있습니다. 컴파일러는 `@boundscheck` 블록을 *호출 함수에 인라인될 경우에만* 제거합니다. 예를 들어, `sum` 메서드를 다음과 같이 작성할 수 있습니다:

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in eachindex(A)
        @inbounds r += A[i]
    end
    return r
end
```

사용자 정의 배열 유사 타입 `MyArray`가 다음과 같이 있습니다:

```julia
@inline getindex(A::MyArray, i::Real) = (@boundscheck checkbounds(A, i); A.data[to_index(i)])
```

그렇다면 `getindex`가 `sum`에 인라인될 때, `checkbounds(A, i)` 호출은 생략됩니다. 함수에 여러 레이어의 인라인이 포함되어 있는 경우, `@boundscheck` 블록은 최대 한 레벨의 인라인 깊이에서만 제거됩니다. 이 규칙은 스택 위쪽의 코드에서 의도하지 않은 프로그램 동작 변경을 방지합니다.

### Caution!

`@inbounds`를 사용하면 안전하지 않은 작업을 우연히 노출하기 쉽습니다. 위의 예제를 다음과 같이 작성하고 싶을 수 있습니다.

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in 1:length(A)
        @inbounds r += A[i]
    end
    return r
end
```

어떤 것은 조용히 1 기반 인덱싱을 가정하고 있으며, 따라서 [`OffsetArrays`](@ref man-custom-indices)와 함께 사용될 때 안전하지 않은 메모리 접근을 노출합니다:

```julia-repl
julia> using OffsetArrays

julia> sum(OffsetArray([1, 2, 3], -10))
9164911648 # inconsistent results or segfault
```

원래 오류의 원천은 `1:length(A)`이지만, `@inbounds`의 사용은 경계 오류의 결과를 덜 쉽게 포착하고 디버깅할 수 있는 안전하지 않은 메모리 접근으로 증가시킵니다. `@inbounds`를 사용하는 메서드가 안전하다는 것을 증명하는 것은 종종 어렵거나 불가능하므로, 성능 향상의 이점을 세그폴트 및 조용한 오작동의 위험과 비교해야 합니다. 특히 공개 API에서는 더욱 그렇습니다.

## Propagating inbounds

코드 조직상의 이유로 `@inbounds`와 `@boundscheck` 선언 사이에 여러 레이어를 두고 싶을 수 있는 특정 시나리오가 있을 수 있습니다. 예를 들어, 기본 `getindex` 메서드는 `getindex(A::AbstractArray, i::Real)`가 `getindex(IndexStyle(A), A, i)`를 호출하고, 이는 다시 `_getindex(::IndexLinear, A, i)`를 호출하는 체인을 가지고 있습니다.

"한 겹의 인라인 규칙"을 무시하기 위해, 함수는 [`Base.@propagate_inbounds`](@ref)로 표시될 수 있으며, 이를 통해 추가적인 인라인 계층을 통해 인바운드 컨텍스트(또는 아웃 오브 바운드 컨텍스트)를 전파할 수 있습니다.

## The bounds checking call hierarchy

전체 계층 구조는:

  * `checkbounds(A, I...)`는 호출합니다.

      * `checkbounds(Bool, A, I...)`는 호출합니다.

          * `checkbounds_indices(Bool, axes(A), I)`는 재귀적으로 호출합니다.

              * `checkindex` 각 차원에 대해

여기 `A`는 배열이고, `I`는 "요청된" 인덱스를 포함합니다. `axes(A)`는 `A`의 "허용된" 인덱스의 튜플을 반환합니다.

`checkbounds(A, I...)`는 인덱스가 유효하지 않을 경우 오류를 발생시키고, 반면에 `checkbounds(Bool, A, I...)`는 그런 경우에 `false`를 반환합니다. `checkbounds_indices`는 배열에 대한 정보 중 `axes` 튜플을 제외한 모든 정보를 버리고, 순수한 인덱스 대 인덱스 비교를 수행합니다: 이는 상대적으로 적은 수의 컴파일된 메서드가 다양한 배열 유형을 처리할 수 있게 합니다. 인덱스는 튜플로 지정되며, 일반적으로 개별 차원은 또 다른 중요한 함수인 `checkindex`를 호출하여 1-1 방식으로 비교됩니다: 일반적으로,

```julia
checkbounds_indices(Bool, (IA1, IA...), (I1, I...)) = checkindex(Bool, IA1, I1) &
                                                      checkbounds_indices(Bool, IA, I)
```

그래서 `checkindex`는 단일 차원을 확인합니다. 이 모든 함수, 비공식적으로 내보내지 않는 `checkbounds_indices`를 포함하여, `?`를 사용하여 접근할 수 있는 문서 문자열이 있습니다.

특정 배열 유형에 대한 경계 검사를 사용자 정의해야 하는 경우 `checkbounds(Bool, A, I...)`를 특수화해야 합니다. 그러나 대부분의 경우 배열 유형에 유용한 `axes`를 제공하는 한 `checkbounds_indices`에 의존할 수 있어야 합니다.

새로운 인덱스 유형이 있는 경우, 먼저 배열의 특정 차원에 대한 단일 인덱스를 처리하는 `checkindex`를 특수화하는 것을 고려하십시오. 사용자 정의 다차원 인덱스 유형(예: `CartesianIndex`와 유사)이 있는 경우, `checkbounds_indices`를 특수화하는 것을 고려해야 할 수도 있습니다.

이 계층 구조는 메서드 모호성을 줄이기 위해 설계되었습니다. 우리는 `checkbounds`가 배열 유형에 특화된 장소가 되도록 하려고 하며, 인덱스 유형에 대한 특화는 피하려고 합니다. 반대로, `checkindex`는 인덱스 유형(특히 마지막 인수)에만 특화되도록 의도되었습니다.

## Emit bounds checks

줄리아는 `--check-bounds={yes|no|auto}`로 실행할 수 있으며, 이를 통해 항상, 절대, 또는 `@inbounds` 선언을 존중하여 경계 검사를 수행합니다.
