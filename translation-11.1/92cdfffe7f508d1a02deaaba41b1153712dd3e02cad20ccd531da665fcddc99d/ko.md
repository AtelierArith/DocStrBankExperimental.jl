```
Base.hasfastin(T)
```

`collection::T`에서 `x ∈ collection` 계산이 "빠른" 작업(일반적으로 상수 또는 로그 복잡도)으로 간주될 수 있는지 여부를 결정합니다. 편의를 위해 `hasfastin(x) = hasfastin(typeof(x))`가 제공되므로 인스턴스를 타입 대신 전달할 수 있습니다. 그러나 타입 인수를 수용하는 형태는 새로운 타입에 대해 정의되어야 합니다.

`hasfastin(T)`의 기본값은 [`AbstractSet`](@ref), [`AbstractDict`](@ref) 및 [`AbstractRange`](@ref)의 하위 타입에 대해 `true`이며, 그렇지 않은 경우 `false`입니다.
