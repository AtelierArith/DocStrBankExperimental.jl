# SubArrays

줄리아의 `SubArray` 타입은 부모 [`AbstractArray`](@ref)의 "뷰"를 인코딩하는 컨테이너입니다. 이 페이지는 `SubArray`의 일부 설계 원칙과 구현을 문서화합니다.

주요 설계 목표 중 하나는 [`IndexLinear`](@ref) 및 [`IndexCartesian`](@ref) 배열의 뷰에 대해 높은 성능을 보장하는 것입니다. 또한, `IndexLinear` 배열의 뷰는 가능한 한 `IndexLinear`여야 합니다.

## Index replacement

3D 배열의 2D 슬라이스 만들기:

```@meta
DocTestSetup = :(import Random; Random.seed!(1234))
```

```jldoctest subarray
julia> A = rand(2,3,4);

julia> S1 = view(A, :, 1, 2:3)
2×2 view(::Array{Float64, 3}, :, 1, 2:3) with eltype Float64:
 0.839622  0.711389
 0.967143  0.103929

julia> S2 = view(A, 1, :, 2:3)
3×2 view(::Array{Float64, 3}, 1, :, 2:3) with eltype Float64:
 0.839622  0.711389
 0.789764  0.806704
 0.566704  0.962715
```

```@meta
DocTestSetup = nothing
```

`view`는 "싱글톤" 차원(정수로 지정된 차원)을 제거하므로, `S1`과 `S2`는 모두 2차원 `SubArray`입니다. 따라서 이들을 인덱싱하는 자연스러운 방법은 `S1[i,j]`입니다. 부모 배열 `A`에서 값을 추출하는 자연스러운 접근 방식은 `S1[i,j]`를 `A[i,1,(2:3)[j]]`로, `S2[i,j]`를 `A[1,i,(2:3)[j]]`로 대체하는 것입니다.

SubArrays 디자인의 주요 특징은 이 인덱스 교체가 런타임 오버헤드 없이 수행될 수 있다는 것입니다.

## SubArray design

### Type parameters and fields

채택된 전략은 무엇보다 먼저 유형의 정의에서 표현됩니다:

```julia
struct SubArray{T,N,P,I,L} <: AbstractArray{T,N}
    parent::P
    indices::I
    offset1::Int       # for linear indexing and pointer, only valid when L==true
    stride1::Int       # used only for linear indexing
    ...
end
```

`SubArray`는 5개의 타입 매개변수를 가지고 있습니다. 첫 번째 두 개는 표준 요소 타입과 차원 수입니다. 다음은 부모 `AbstractArray`의 타입입니다. 가장 많이 사용되는 것은 네 번째 매개변수로, 각 차원의 인덱스 타입을 나타내는 `Tuple`입니다. 마지막으로, `L`은 디스패치를 위한 편의로 제공되며, 인덱스 타입이 빠른 선형 인덱싱을 지원하는지를 나타내는 불리언입니다. 이에 대한 자세한 내용은 나중에 다루겠습니다.

만약 위의 예에서 `A`가 `Array{Float64, 3}`이라면, 위의 `S1` 경우는 `SubArray{Float64,2,Array{Float64,3},Tuple{Base.Slice{Base.OneTo{Int64}},Int64,UnitRange{Int64}},false}`가 될 것입니다. 특히, `S1`을 생성하는 데 사용된 인덱스의 유형을 저장하는 튜플 매개변수에 주목하십시오. 마찬가지로,

```jldoctest subarray
julia> S1.indices
(Base.Slice(Base.OneTo(2)), 1, 2:3)
```

이러한 값을 저장하면 인덱스 교체가 가능하고, 유형이 매개변수로 인코딩되어 있으면 효율적인 알고리즘으로 디스패치할 수 있습니다.

### Index translation

인덱스 변환을 수행하려면 서로 다른 구체적인 `SubArray` 유형에 대해 다른 작업을 수행해야 합니다. 예를 들어, `S1`의 경우 `i,j` 인덱스를 부모 배열의 첫 번째 및 세 번째 차원에 적용해야 하고, `S2`의 경우 두 번째 및 세 번째 차원에 적용해야 합니다. 인덱싱에 대한 가장 간단한 접근 방식은 런타임에 유형 분석을 수행하는 것입니다:

```julia
parentindices = Vector{Any}()
for thisindex in S.indices
    ...
    if isa(thisindex, Int)
        # Don't consume one of the input indices
        push!(parentindices, thisindex)
    elseif isa(thisindex, AbstractVector)
        # Consume an input index
        push!(parentindices, thisindex[inputindex[j]])
        j += 1
    elseif isa(thisindex, AbstractMatrix)
        # Consume two input indices
        push!(parentindices, thisindex[inputindex[j], inputindex[j+1]])
        j += 2
    elseif ...
end
S.parent[parentindices...]
```

불행히도, 이는 성능 측면에서 재앙적일 것입니다: 각 요소 접근은 메모리를 할당하고, 많은 잘못된 타입의 코드 실행을 포함합니다.

더 나은 접근 방식은 각 유형의 저장된 인덱스를 처리하기 위해 특정 메서드로 디스패치하는 것입니다. 그것이 `reindex`가 하는 일입니다: 첫 번째 저장된 인덱스의 유형에 따라 디스패치하고 적절한 수의 입력 인덱스를 소비한 다음, 나머지 인덱스에 대해 재귀적으로 호출합니다. `S1`의 경우, 이는 다음과 같이 확장됩니다.

```julia
Base.reindex(S1, S1.indices, (i, j)) == (i, S1.indices[2], S1.indices[3][j])
```

모든 인덱스 쌍 `(i,j)`에 대해 (아래에 설명된 [`CartesianIndex`](@ref) 및 그 배열을 제외하고).

이것은 `SubArray`의 핵심입니다; 인덱싱 방법은 이 인덱스 변환을 수행하기 위해 `reindex`에 의존합니다. 그러나 때때로 우리는 간접 참조를 피하고 더 빠르게 만들 수 있습니다.

### Linear indexing

선형 인덱싱은 전체 배열이 연속적인 요소를 구분하는 단일 보폭을 가질 때 효율적으로 구현될 수 있으며, 이는 특정 오프셋에서 시작합니다. 이는 이러한 값을 미리 계산할 수 있음을 의미하며, 선형 인덱싱을 단순히 덧셈과 곱셈으로 표현할 수 있어 `reindex`의 간접 참조와 (더 중요한 것은) 데카르트 좌표의 느린 계산을 완전히 피할 수 있습니다.

`SubArray` 유형의 경우, 효율적인 선형 인덱싱의 가용성은 인덱스의 유형에만 기반하며, 부모 배열의 크기와 같은 값에 의존하지 않습니다. 주어진 인덱스 집합이 내부 `Base.viewindexing` 함수를 사용하여 빠른 선형 인덱싱을 지원하는지 여부를 물어볼 수 있습니다:

```jldoctest subarray
julia> Base.viewindexing(S1.indices)
IndexCartesian()

julia> Base.viewindexing(S2.indices)
IndexLinear()
```

이것은 `SubArray`의 생성 중에 계산되며, 빠른 선형 인덱싱 지원을 인코딩하는 부울 값으로 `L` 타입 매개변수에 저장됩니다. 엄밀히 필요하지는 않지만, 이를 통해 중개자 없이 `SubArray{T,N,A,I,true}`에 대해 직접 디스패치를 정의할 수 있습니다.

이 계산은 런타임 값에 의존하지 않기 때문에 보폭이 균일한 경우를 놓칠 수 있습니다:

```jldoctest
julia> A = reshape(1:4*2, 4, 2)
4×2 reshape(::UnitRange{Int64}, 4, 2) with eltype Int64:
 1  5
 2  6
 3  7
 4  8

julia> diff(A[2:2:4,:][:])
3-element Vector{Int64}:
 2
 2
 2
```

`view(A, 2:2:4, :)`로 구성된 뷰는 균일한 보폭을 가지므로 선형 인덱싱을 효율적으로 수행할 수 있습니다. 그러나 이 경우의 성공은 배열의 크기에 따라 달라집니다: 만약 첫 번째 차원이 홀수였다면,

```jldoctest
julia> A = reshape(1:5*2, 5, 2)
5×2 reshape(::UnitRange{Int64}, 5, 2) with eltype Int64:
 1   6
 2   7
 3   8
 4   9
 5  10

julia> diff(A[2:2:4,:][:])
3-element Vector{Int64}:
 2
 3
 2
```

그렇다면 `A[2:2:4,:]`는 균일한 보폭을 가지지 않으므로 효율적인 선형 인덱싱을 보장할 수 없습니다. `SubArray`의 매개변수에 인코딩된 유형만을 기반으로 이 결정을 내려야 하므로, `S = view(A, 2:2:4, :)`는 효율적인 선형 인덱싱을 구현할 수 없습니다.

### A few details

  * `Base.reindex` 함수는 입력 인덱스의 유형에 구애받지 않습니다. 이 함수는 저장된 인덱스를 어떻게 그리고 어디에서 재인덱싱해야 하는지를 결정합니다. 이 함수는 정수 인덱스뿐만 아니라 비스칼라 인덱싱도 지원합니다. 이는 뷰의 뷰가 두 수준의 간접 참조를 필요로 하지 않음을 의미하며, 원래 부모 배열로의 인덱스를 단순히 재계산할 수 있습니다!
  * 이제 슬라이스를 지원하는 것이 매개변수 `N`에 의해 주어진 차원이 부모 배열의 차원이나 `indices` 튜플의 길이와 반드시 같지 않다는 것이 꽤 명확해졌기를 바랍니다. 사용자 제공 인덱스가 반드시 `indices` 튜플의 항목과 일치하지도 않습니다(예: 두 번째 사용자 제공 인덱스는 부모 배열의 세 번째 차원에 해당할 수 있으며, `indices` 튜플의 세 번째 요소와 일치할 수 있습니다).

    저장된 부모 배열의 차원 수는 `indices` 튜플의 유효한 인덱스 수와 같아야 한다는 점은 덜 명확할 수 있습니다. 몇 가지 예:

    ```julia
    A = reshape(1:35, 5, 7) # A 2d parent Array
    S = view(A, 2:7)         # A 1d view created by linear indexing
    S = view(A, :, :, 1:1)   # Appending extra indices is supported
    ```

    순진하게 생각하면 `S.parent = A`와 `S.indices = (:,:,1:1)`만 설정하면 될 것 같지만, 이는 재색인 프로세스를 극적으로 복잡하게 만듭니다. 특히 뷰의 뷰에 대해서는 더욱 그렇습니다. 저장된 인덱스의 유형에 따라 분기해야 할 뿐만 아니라, 주어진 인덱스가 최종 인덱스인지 확인하고 남아 있는 저장된 인덱스를 "병합"해야 합니다. 이는 쉬운 작업이 아니며, 더 나쁜 점은 선형 인덱싱에 암묵적으로 의존하기 때문에 느립니다.

    다행히도, 이것이 바로 `ReshapedArray`가 수행하는 계산이며, 가능하다면 선형적으로 수행됩니다. 따라서 `view`는 필요한 경우 부모 배열을 주어진 인덱스에 적합한 차원으로 재구성하여 보장합니다. 내부 `SubArray` 생성자는 이 불변성이 만족되도록 보장합니다.
  * [`CartesianIndex`](@ref) 및 그 배열은 `reindex` 계획에 심각한 문제를 일으킵니다. `reindex`는 저장된 인덱스의 유형에 따라 얼마나 많은 전달된 인덱스를 사용해야 하는지와 그들이 어디로 가야 하는지를 결정하기 위해 단순히 분배됩니다. 그러나 `CartesianIndex`가 있으면 전달된 인수의 수와 그들이 인덱싱하는 차원의 수 사이에 더 이상 일대일 대응이 없습니다. 위의 예인 `Base.reindex(S1, S1.indices, (i, j))`로 돌아가면, `i, j = CartesianIndex(), CartesianIndex(2,1)`에 대한 확장이 잘못되었음을 알 수 있습니다. `CartesianIndex()`를 완전히 *건너뛰고* 다음을 반환해야 합니다:

    ```julia
    (CartesianIndex(2,1)[1], S1.indices[2], S1.indices[3][CartesianIndex(2,1)[2]])
    ```

    대신, 우리는 다음을 얻습니다:

    ```julia
    (CartesianIndex(), S1.indices[2], S1.indices[3][CartesianIndex(2,1)])
    ```

    이 작업을 올바르게 수행하려면 모든 차원 조합에 걸쳐 저장된 인덱스와 전달된 인덱스에 대해 *결합된* 디스패치가 필요합니다. 따라서 `reindex`는 `CartesianIndex` 인덱스와 함께 호출되어서는 안 됩니다. 다행히도 스칼라 경우는 `CartesianIndex` 인수를 평범한 정수로 먼저 평탄화하여 쉽게 처리할 수 있습니다. 그러나 `CartesianIndex` 배열은 그렇게 쉽게 직교 조각으로 나눌 수 없습니다. `reindex`를 사용하기 전에 `view`는 인수 목록에 `CartesianIndex` 배열이 없도록 확인해야 합니다. 만약 있다면, `reindex` 계산을 완전히 피하고 두 수준의 간접성을 가진 중첩 `SubArray`를 구성하여 "펀트"할 수 있습니다.
