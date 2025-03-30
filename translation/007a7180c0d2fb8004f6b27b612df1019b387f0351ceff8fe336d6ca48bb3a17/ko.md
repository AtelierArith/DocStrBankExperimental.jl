```
Core.memoryrefsetonce!(::GenericMemoryRef, value,
                       success_order::Symbol, fail_order::Symbol=success_order, boundscheck::Bool) -> success::Bool
```

주어진 값으로 `MemoryRef`를 설정하는 작업을 원자적으로 수행하며, 이전에 설정되지 않은 경우에만 수행합니다.

!!! compat "Julia 1.11"
    이 함수는 Julia 1.11 이상이 필요합니다.


또한 [`setpropertyonce!`](@ref Base.replaceproperty!) 및 [`Core.memoryrefset!`](@ref)를 참조하십시오.
