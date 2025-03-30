```
similar(array, [element_type=eltype(array)], [dims=size(array)])
```

주어진 원본 배열을 기반으로 지정된 요소 유형과 크기로 초기화되지 않은 가변 배열을 생성합니다. 두 번째 및 세 번째 인수는 모두 선택 사항이며, 주어진 배열의 `eltype` 및 `size`로 기본값이 설정됩니다. 차원은 단일 튜플 인수로 지정하거나 일련의 정수 인수로 지정할 수 있습니다.

사용자 정의 AbstractArray 하위 유형은 주어진 요소 유형과 차원에 가장 적합한 배열 유형을 선택할 수 있습니다. 이 메서드를 전문화하지 않으면 기본값은 `Array{element_type}(undef, dims...)`입니다.

예를 들어, `similar(1:10, 1, 4)`는 범위가 가변적이지 않으며 2차원을 지원하지 않기 때문에 초기화되지 않은 `Array{Int,2}`를 반환합니다:

```julia-repl
julia> similar(1:10, 1, 4)
1×4 Matrix{Int64}:
 4419743872  4374413872  4419743888  0
```

반대로, `similar(trues(10,10), 2)`는 두 개의 요소를 가진 초기화되지 않은 `BitVector`를 반환합니다. `BitArray`는 가변적이며 1차원 배열을 지원할 수 있습니다:

```julia-repl
julia> similar(trues(10,10), 2)
2-element BitVector:
 0
 0
```

그러나 `BitArray`는 [`Bool`](@ref) 유형의 요소만 저장할 수 있으므로, 다른 요소 유형을 요청하면 일반 `Array`가 대신 생성됩니다:

```julia-repl
julia> similar(falses(10), Float64, 2, 4)
2×4 Matrix{Float64}:
 2.18425e-314  2.18425e-314  2.18425e-314  2.18425e-314
 2.18425e-314  2.18425e-314  2.18425e-314  2.18425e-314
```

자세한 내용은: [`undef`](@ref), [`isassigned`](@ref).
