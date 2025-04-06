```
ord(lt, by, rev::Union{Bool, Nothing}, order::Ordering=Forward)
```

[`Ordering`](@ref) 객체를 [`sort!`](@ref)에서 사용된 것과 동일한 인수로 구성합니다. 요소는 먼저 `by` 함수(이는 [`identity`](@ref)일 수 있음)에 의해 변환된 다음, `lt` 함수 또는 기존의 정렬 `order`에 따라 비교됩니다. `lt`는 [`isless`](@ref) 또는 [`sort!`](@ref)의 `lt` 매개변수와 동일한 규칙을 준수하는 함수여야 합니다. 마지막으로, 결과 정렬은 `rev=true`인 경우 반전됩니다.

`isless`가 아닌 `lt`와 [`Base.Order.Forward`](@ref) 또는 [`Base.Order.Reverse`](@ref)가 아닌 `order`를 함께 사용하는 것은 허용되지 않으며, 그렇지 않으면 모든 옵션은 독립적이며 가능한 모든 조합에서 함께 사용할 수 있습니다.
