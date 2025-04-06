```
eachindex(A...)
eachindex(::IndexStyle, A::AbstractArray...)
```

`AbstractArray` `A`의 각 인덱스를 효율적으로 방문하기 위한 반복 가능한 객체를 생성합니다. 빠른 선형 인덱싱을 선택한 배열 유형(예: `Array`)의 경우, 이는 1 기반 인덱싱을 사용하는 경우 단순히 `1:length(A)` 범위입니다. 빠른 선형 인덱싱을 선택하지 않은 배열 유형의 경우, 일반적으로 모든 차원에 대해 지정된 인덱스로 배열에 효율적으로 인덱싱하기 위해 특수화된 카르테시안 범위가 반환됩니다.

일반적으로 `eachindex`는 문자열 및 사전을 포함한 임의의 반복 가능한 객체를 허용하며, 임의의 인덱스 유형(예: 불균형 간격 또는 비정수 인덱스)을 지원하는 반복자 객체를 반환합니다.

`A`가 `AbstractArray`인 경우, `eachindex`가 반환해야 하는 인덱스 스타일을 명시적으로 지정할 수 있으며, 첫 번째 인수로 `IndexStyle` 유형의 값을 전달합니다(일반적으로 선형 인덱스가 필요한 경우 `IndexLinear()` 또는 카르테시안 범위가 필요한 경우 `IndexCartesian()`).

하나 이상의 `AbstractArray` 인수를 제공하면, `eachindex`는 모든 인수에 대해 빠른 반복 가능한 객체를 생성합니다(일반적으로 모든 입력이 빠른 선형 인덱싱을 가지면 [`UnitRange`](@ref), 그렇지 않으면 [`CartesianIndices`](@ref)). 배열의 크기 및/또는 차원이 다르면 `DimensionMismatch` 예외가 발생합니다.

인덱스와 값을 함께 반복하려면 [`pairs`](@ref)`(A)`를 참조하고, 한 차원에 대한 유효한 인덱스를 보려면 [`axes`](@ref)`(A, 2)`를 참조하십시오.

# 예제

```jldoctest
julia> A = [10 20; 30 40];

julia> for i in eachindex(A) # 선형 인덱싱
           println("A[", i, "] == ", A[i])
       end
A[1] == 10
A[2] == 30
A[3] == 20
A[4] == 40

julia> for i in eachindex(view(A, 1:2, 1:1)) # 카르테시안 인덱싱
           println(i)
       end
CartesianIndex(1, 1)
CartesianIndex(2, 1)
```
