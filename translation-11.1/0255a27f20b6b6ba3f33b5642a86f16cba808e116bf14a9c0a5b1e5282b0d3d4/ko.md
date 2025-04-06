```
reinterpret(T::DataType, A::AbstractArray)
```

주어진 배열과 동일한 이진 데이터를 가진 배열의 뷰를 생성하지만, `T`를 요소 유형으로 사용합니다.

이 함수는 요소가 명시적으로 검색될 때까지 계산되지 않는 "지연" 배열에서도 작동합니다. 예를 들어, 범위 `1:6`에 대한 `reinterpret`는 조밀한 벡터 `collect(1:6)`에 대한 것과 유사하게 작동합니다:

```jldoctest
julia> reinterpret(Float32, UInt32[1 2 3 4 5])
1×5 reinterpret(Float32, ::Matrix{UInt32}):
 1.0f-45  3.0f-45  4.0f-45  6.0f-45  7.0f-45

julia> reinterpret(Complex{Int}, 1:6)
3-element reinterpret(Complex{Int64}, ::UnitRange{Int64}):
 1 + 2im
 3 + 4im
 5 + 6im
```

패딩 비트의 위치가 `T`와 `eltype(A)` 사이에 정렬되지 않으면, 결과 배열은 읽기 전용 또는 쓰기 전용이 되어, 각각 잘못된 비트가 쓰이거나 읽히는 것을 방지합니다.

```jldoctest
julia> a = reinterpret(Tuple{UInt8, UInt32}, UInt32[1, 2])
1-element reinterpret(Tuple{UInt8, UInt32}, ::Vector{UInt32}):
 (0x01, 0x00000002)

julia> a[1] = 3
ERROR: Padding of type Tuple{UInt8, UInt32} is not compatible with type UInt32.

julia> b = reinterpret(UInt32, Tuple{UInt8, UInt32}[(0x01, 0x00000002)]); # showing will error

julia> b[1]
ERROR: Padding of type UInt32 is not compatible with type Tuple{UInt8, UInt32}.
```
