```
supertypes(T::Type)
```

`T`와 모든 상위 타입의 튜플 `(T, ..., Any)`를 반환합니다. 이는 [`supertype`](@ref) 함수를 연속적으로 호출하여 결정되며, `<:` 순서로 나열되고 `Any`로 종료됩니다.

또한 [`subtypes`](@ref)를 참조하세요.

# 예시

```jldoctest
julia> supertypes(Int)
(Int64, Signed, Integer, Real, Number, Any)
```
