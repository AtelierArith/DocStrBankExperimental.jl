```
IteratorEltype(itertype::Type) -> IteratorEltype
```

주어진 반복자의 유형에 따라 다음 값 중 하나를 반환합니다:

  * `EltypeUnknown()` - 반복자가 생성하는 요소의 유형이 미리 알려져 있지 않은 경우.
  * `HasEltype()` - 요소 유형이 알려져 있으며, [`eltype`](@ref)가 의미 있는 값을 반환할 경우.

`HasEltype()`는 기본값이며, 반복자는 [`eltype`](@ref)를 구현하는 것으로 가정됩니다.

이 특성은 일반적으로 특정 유형의 결과를 미리 할당하는 알고리즘과 생성된 값의 유형에 따라 결과 유형을 선택하는 알고리즘 간의 선택에 사용됩니다.

```jldoctest
julia> Base.IteratorEltype(1:5)
Base.HasEltype()
```
