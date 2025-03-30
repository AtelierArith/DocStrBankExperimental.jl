```
Core.memoryrefreplace!(::GenericMemoryRef, expected, desired,
                       success_order::Symbol, fail_order::Symbol=success_order, boundscheck::Bool) -> (; old, success::Bool)
```

원자적으로 `MemoryRef` 값을 가져오고 조건부로 설정하는 작업을 수행합니다.

!!! compat "Julia 1.11"
    이 함수는 Julia 1.11 이상이 필요합니다.


또한 [`replaceproperty!`](@ref Base.replaceproperty!) 및 [`Core.memoryrefset!`](@ref)를 참조하십시오.
