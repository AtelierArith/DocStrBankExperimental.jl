```
IteratorSize(itertype::Type) -> IteratorSize
```

주어진 반복자의 유형에 따라 다음 값 중 하나를 반환합니다:

  * `SizeUnknown()` - 길이(요소 수)를 미리 결정할 수 없는 경우.
  * `HasLength()` - 고정된 유한 길이가 있는 경우.
  * `HasShape{N}()` - 알려진 길이와 다차원 형태(배열과 같은 개념)가 있는 경우. 이 경우 `N`은 차원의 수를 나타내며, [`axes`](@ref) 함수는 반복자에 대해 유효합니다.
  * `IsInfinite()` - 반복자가 값을 무한히 생성하는 경우.

기본값(이 함수를 정의하지 않는 반복자에 대한)은 `HasLength()`입니다. 이는 대부분의 반복자가 [`length`](@ref)를 구현한다고 가정함을 의미합니다.

이 특성은 일반적으로 결과를 위해 공간을 미리 할당하는 알고리즘과 결과를 점진적으로 크기를 조정하는 알고리즘 간의 선택에 사용됩니다.

```jldoctest
julia> Base.IteratorSize(1:5)
Base.HasShape{1}()

julia> Base.IteratorSize((2,3))
Base.HasLength()
```
