```
eigvals!(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> values
```

[`eigvals`](@ref)와 동일하지만, 복사본을 생성하는 대신 입력 `A`를 덮어써서 공간을 절약합니다. `irange`는 검색할 고유값 *인덱스*의 범위입니다 - 예를 들어, 2번째에서 8번째 고유값까지입니다.
