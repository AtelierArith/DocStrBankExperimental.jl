```
Core.memoryref_isassigned(::GenericMemoryRef, ordering::Symbol, boundscheck::Bool)
```

`MemoryRef`에 저장된 값이 있는지 여부를 반환하며, `Memory`가 비어 있으면 false를 반환합니다. [`isassigned(::Base.RefValue)`](@ref), [`Core.memoryrefget`](@ref)를 참조하십시오. 지정된 메모리 순서는 `isatomic` 매개변수와 호환되어야 합니다.

!!! compat "Julia 1.11"
    이 함수는 Julia 1.11 이상이 필요합니다.

