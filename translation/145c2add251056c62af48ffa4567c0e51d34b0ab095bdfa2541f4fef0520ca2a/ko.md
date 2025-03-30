# [Arrays with custom indices](@id man-custom-indices)

전통적으로, 줄리아의 배열은 1부터 인덱싱되지만, 일부 다른 언어는 0부터 번호를 매기기 시작하고, 또 다른 언어(예: 포트란)는 임의의 시작 인덱스를 지정할 수 있습니다. 표준을 선택하는 데(즉, 줄리아의 경우 1) 많은 장점이 있지만, `1:size(A,d)` 범위를 벗어나 인덱싱할 수 있다면 상당히 단순해지는 알고리즘이 있습니다(그리고 `0:size(A,d)-1`만이 아닙니다). 이러한 계산을 용이하게 하기 위해, 줄리아는 임의의 인덱스를 가진 배열을 지원합니다.

이 페이지의 목적은 "내 코드에서 이러한 배열을 지원하기 위해 무엇을 해야 합니까?"라는 질문에 답하는 것입니다. 먼저 가장 간단한 경우를 살펴보겠습니다. 코드가 비전통적인 인덱싱을 사용하는 배열을 처리할 필요가 없다는 것을 알고 있다면, 답은 "아무것도 하지 않음"이기를 바랍니다. 전통적인 배열을 사용하는 오래된 코드는 Julia의 내보낸 인터페이스를 사용하고 있는 한 본질적으로 수정 없이 작동해야 합니다. 인덱싱이 1에서 시작하는 전통적인 배열을 사용자에게 강제로 제공하는 것이 더 편리하다면, 다음을 추가할 수 있습니다.

```julia
Base.require_one_based_indexing(arrays...)
```

여기서 `arrays...`는 1 기반 인덱싱을 위반하는지 확인하고자 하는 배열 객체의 목록입니다.

## Generalizing existing code

개요로서, 단계는 다음과 같습니다:

  * `size`를 `axes`로 여러 번 교체하세요.
  * `1:length(A)`를 `eachindex(A)`로 교체하거나, 경우에 따라 `LinearIndices(A)`로 교체하세요.
  * 명시적 할당을 `Array{Int}(undef, size(B))`에서 `similar(Array{Int}, axes(B))`로 교체하세요.

아래에서 더 자세히 설명됩니다.

### Things to watch out for

비정형 인덱싱은 모든 배열이 1부터 인덱싱된다고 가정하는 많은 사람들의 가정을 깨기 때문에, 이러한 배열을 사용할 경우 오류가 발생할 가능성이 항상 존재합니다. 가장 짜증나는 버그는 잘못된 결과나 세그멘테이션 오류(줄리아의 전체 충돌)일 것입니다. 예를 들어, 다음 함수를 고려해 보십시오:

```julia
function mycopy!(dest::AbstractVector, src::AbstractVector)
    length(dest) == length(src) || throw(DimensionMismatch("vectors must match"))
    # OK, now we're safe to use @inbounds, right? (not anymore!)
    for i = 1:length(src)
        @inbounds dest[i] = src[i]
    end
    dest
end
```

이 코드는 벡터가 1부터 인덱싱된다고 암묵적으로 가정합니다. 만약 `dest`가 `src`와 다른 인덱스에서 시작한다면, 이 코드가 세그멘테이션 오류를 발생시킬 가능성이 있습니다. (세그멘테이션 오류가 발생하면, 원인을 찾기 위해 `--check-bounds=yes` 옵션으로 줄리아를 실행해 보세요.)

### Using `axes` for bounds checks and loop iteration

`axes(A)` (reminiscent of `size(A)`)는 `A`의 각 차원에 대한 유효한 인덱스의 범위를 지정하는 `AbstractUnitRange{<:Integer}` 객체의 튜플을 반환합니다. `A`가 비정상적인 인덱싱을 가질 경우, 범위는 1에서 시작하지 않을 수 있습니다. 특정 차원 `d`에 대한 범위만 원할 경우, `axes(A, d)`를 사용하면 됩니다.

Base는 `OneTo`라는 사용자 정의 범위 유형을 구현합니다. 여기서 `OneTo(n)`은 `1:n`과 동일한 의미를 가지지만, 타입 시스템을 통해 하한 인덱스가 1임을 보장하는 형식입니다. 새로운 [`AbstractArray`](@ref) 유형에 대해, 이는 `axes`에 의해 반환되는 기본값이며, 이 배열 유형이 "전통적인" 1 기반 인덱싱을 사용함을 나타냅니다.

경계 검사를 위해, `checkbounds` 및 `checkindex`라는 전용 함수가 있으며, 이러한 테스트를 간소화할 수 있습니다.

### Linear indexing (`LinearIndices`)

일부 알고리즘은 다차원 배열 `A`에 대해서도 단일 선형 인덱스 `A[i]`로 가장 편리하게(또는 효율적으로) 작성됩니다. 배열의 고유 인덱스와 관계없이 선형 인덱스는 항상 `1:length(A)` 범위를 가집니다. 그러나 이는 일차원 배열(즉, [`AbstractVector`](@ref))에 대한 모호성을 발생시킵니다: `v[i]`는 선형 인덱싱을 의미합니까, 아니면 배열의 고유 인덱스를 사용한 카르테시안 인덱싱을 의미합니까?

이러한 이유로, 최선의 선택은 `eachindex(A)`를 사용하여 배열을 반복하는 것이거나, 인덱스가 연속된 정수여야 하는 경우 `LinearIndices(A)`를 호출하여 인덱스 범위를 얻는 것입니다. A가 AbstractVector인 경우 `axes(A, 1)`을 반환하며, 그렇지 않은 경우 `1:length(A)`와 동일한 결과를 반환합니다.

이 정의에 따르면, 1차원 배열은 항상 배열의 기본 인덱스를 사용하여 카르테시안 인덱싱을 사용합니다. 이를 강화하기 위해, 인덱스 변환 함수는 모양이 비전통적인 인덱싱(즉, `Tuple{UnitRange}`인 경우)인 1차원 배열을 나타내면 오류를 발생시킨다는 점에 유의할 가치가 있습니다. 전통적인 인덱싱을 가진 배열의 경우, 이러한 함수는 항상처럼 계속 작동합니다.

`axes`와 `LinearIndices`를 사용하여 `mycopy!`를 다음과 같이 다시 작성할 수 있습니다:

```julia
function mycopy!(dest::AbstractVector, src::AbstractVector)
    axes(dest) == axes(src) || throw(DimensionMismatch("vectors must match"))
    for i in LinearIndices(src)
        @inbounds dest[i] = src[i]
    end
    dest
end
```

### Allocating storage using generalizations of `similar`

저장소는 종종 `Array{Int}(undef, dims)` 또는 `similar(A, args...)`로 할당됩니다. 결과가 다른 배열의 인덱스와 일치해야 할 때, 이것만으로는 항상 충분하지 않을 수 있습니다. 이러한 패턴에 대한 일반적인 대체 방법은 `similar(storagetype, shape)`를 사용하는 것입니다. `storagetype`은 원하는 기본 "전통적인" 동작의 종류를 나타내며, 예를 들어 `Array{Int}` 또는 `BitArray` 또는 심지어 `dims->zeros(Float32, dims)` (모두 0인 배열을 할당합니다)일 수 있습니다. `shape`는 결과가 사용하기를 원하는 인덱스를 지정하는 [`Integer`](@ref) 또는 `AbstractUnitRange` 값의 튜플입니다. A의 인덱스와 일치하는 모두 0인 배열을 생성하는 편리한 방법은 단순히 `zeros(A)`입니다.

몇 가지 명시적인 예를 살펴보겠습니다. 먼저, `A`가 일반적인 인덱스를 가진 경우, `similar(Array{Int}, axes(A))`는 `Array{Int}(undef, size(A))`를 호출하게 되어 배열을 반환합니다. 만약 `A`가 비전통적인 인덱싱을 가진 `AbstractArray` 타입이라면, `similar(Array{Int}, axes(A))`는 `A`와 일치하는 형태(인덱스를 포함)로 "작동하는" `Array{Int}`와 같은 것을 반환해야 합니다. (가장 명백한 구현은 `Array{Int}(undef, size(A))`를 할당한 다음, 인덱스를 이동시키는 타입으로 "감싸는" 것입니다.)

또한 `similar(Array{Int}, (axes(A, 2),))`는 `A`의 열 인덱스와 일치하는 `AbstractVector{Int}`(즉, 1차원 배열)를 할당합니다.

## Writing custom array types with non-1 indexing

대부분의 메서드는 모든 `AbstractArray` 유형에 대해 표준입니다. [Abstract Arrays](@ref man-interface-array)를 참조하세요. 이 페이지는 비전통적인 인덱싱을 정의하는 데 필요한 단계에 중점을 둡니다.

### Custom `AbstractUnitRange` types

비-1 인덱스 배열 유형을 작성하는 경우, `axes`를 특수화하여 `UnitRange`를 반환하도록 하거나 (아마도 더 나은 방법으로) 사용자 정의 `AbstractUnitRange`를 반환하도록 해야 합니다. 사용자 정의 유형의 장점은 `similar`와 같은 함수에 대한 할당 유형을 "신호"한다는 것입니다. 인덱싱이 0에서 시작하는 배열 유형을 작성하는 경우, `ZeroRange(n)`이 `0:n-1`과 동등한 새로운 `AbstractUnitRange`, `ZeroRange`를 생성하는 것으로 시작하는 것이 좋습니다.

일반적으로, 패키지에서 `ZeroRange`를 *내보내지 않는* 것이 좋습니다: 다른 패키지들이 자체적으로 `ZeroRange`를 구현할 수 있으며, 여러 개의 서로 다른 `ZeroRange` 유형이 존재하는 것은 (어쩌면 직관에 반하게) 장점입니다: `ModuleA.ZeroRange`는 `similar`가 `ModuleA.ZeroArray`를 생성해야 함을 나타내고, 반면 `ModuleB.ZeroRange`는 `ModuleB.ZeroArray` 유형을 나타냅니다. 이러한 설계는 다양한 사용자 정의 배열 유형 간의 평화로운 공존을 허용합니다.

[CustomUnitRanges.jl](https://github.com/JuliaArrays/CustomUnitRanges.jl)라는 Julia 패키지는 때때로 자신의 `ZeroRange` 타입을 작성할 필요를 피하는 데 사용될 수 있습니다.

### Specializing `axes`

`AbstractUnitRange` 유형을 갖게 되면, `axes`를 특화하십시오:

```julia
Base.axes(A::ZeroArray) = map(n->ZeroRange(n), A.size)
```

여기서 우리는 `ZeroArray`가 `size`라는 필드를 가지고 있다고 상상합니다(이를 구현하는 다른 방법도 있을 것입니다).

일부 경우, `axes(A, d)`에 대한 대체 정의:

```julia
axes(A::AbstractArray{T,N}, d) where {T,N} = d <= N ? axes(A)[d] : OneTo(1)
```

원하는 것이 아닐 수 있습니다: `d > ndims(A)`일 때 `OneTo(1)` 이외의 값을 반환하도록 특화해야 할 수도 있습니다. 마찬가지로, `Base`에는 `axes(A, 1)`과 동등하지만 `ndims(A) > 0`인지 여부를 (런타임에서) 확인하는 것을 피하는 전용 함수 `axes1`이 있습니다. (이는 순수한 성능 최적화입니다.) 정의는 다음과 같습니다:

```julia
axes1(A::AbstractArray{T,0}) where {T} = OneTo(1)
axes1(A::AbstractArray) = axes(A)[1]
```

이 중 첫 번째(0차원 경우)가 사용자 정의 배열 유형에 문제가 된다면, 적절하게 특수화하는 것을 잊지 마세요.

### Specializing `similar`

주어진 사용자 정의 `ZeroRange` 유형에 대해 다음 두 가지 특수화도 `similar`에 추가해야 합니다:

```julia
function Base.similar(A::AbstractArray, T::Type, shape::Tuple{ZeroRange,Vararg{ZeroRange}})
    # body
end

function Base.similar(f::Union{Function,DataType}, shape::Tuple{ZeroRange,Vararg{ZeroRange}})
    # body
end
```

두 가지 모두 사용자 정의 배열 유형을 할당해야 합니다.

### Specializing `reshape`

선택적으로, 메서드를 정의합니다.

```
Base.reshape(A::AbstractArray, shape::Tuple{ZeroRange,Vararg{ZeroRange}}) = ...
```

배열을 `reshape`하여 결과에 사용자 정의 인덱스를 가질 수 있습니다.

### For objects that mimic AbstractArray but are not subtypes

`has_offset_axes`는 호출하는 객체에 대해 `axes`가 정의되어 있어야 합니다. 객체에 대해 `axes` 메서드가 정의되어 있지 않은 이유가 있다면, 메서드를 정의하는 것을 고려해 보세요.

```julia
Base.has_offset_axes(obj::MyNon1IndexedArraylikeObject) = true
```

이것은 1 기반 인덱싱을 가정하는 코드가 문제를 감지하고 유용한 오류를 발생시킬 수 있도록 하여, 잘못된 결과를 반환하거나 세그멘테이션 오류를 발생시키는 대신에 작동하게 합니다.

### Catching errors

새로운 배열 유형이 다른 코드에서 오류를 발생시키는 경우, 유용한 디버깅 단계 중 하나는 `getindex` 및 `setindex!` 구현에서 `@boundscheck`를 주석 처리하는 것입니다. 이렇게 하면 모든 요소 접근이 경계를 확인합니다. 또는 `--check-bounds=yes`로 줄리아를 다시 시작하세요.

일부 경우에는 잘못된 가정을 자주 사용하는 코드가 이러한 함수를 사용하므로 새 배열 유형에 대해 `size`와 `length`를 일시적으로 비활성화하는 것이 도움이 될 수 있습니다.
