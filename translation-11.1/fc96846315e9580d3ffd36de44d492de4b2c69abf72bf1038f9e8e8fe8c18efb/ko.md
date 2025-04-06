```
Core.memoryrefset!(::GenericMemoryRef, value, ordering::Symbol, boundscheck::Bool)
```

`MemoryRef`에 값을 저장하며, `Memory`가 비어있으면 `BoundsError`를 발생시킵니다. `ref[] = value`를 참조하세요. 지정된 메모리 순서는 `isatomic` 매개변수와 호환되어야 합니다.

!!! compat "Julia 1.11"
    이 함수는 Julia 1.11 이상이 필요합니다.

