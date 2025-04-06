```
eltype(type)
```

주어진 `type`의 컬렉션을 반복하여 생성된 요소의 유형을 결정합니다. 사전 유형의 경우, 이는 `Pair{KeyType,ValType}`이 됩니다. 인스턴스를 유형 대신 전달할 수 있도록 편의를 위해 `eltype(x) = eltype(typeof(x))`가 제공됩니다. 그러나 유형 인수를 수용하는 형식은 새 유형에 대해 정의되어야 합니다.

참고: [`keytype`](@ref), [`typeof`](@ref).

# 예제

```jldoctest
julia> eltype(fill(1f0, (2,2)))
Float32

julia> eltype(fill(0x1, (2,2)))
UInt8
```
