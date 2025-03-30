```
Core.memoryrefmodify!(::GenericMemoryRef, op, value, ordering::Symbol, boundscheck::Bool) -> Pair
```

원자적으로 `MemoryRef` 값을 가져오고 설정하는 작업을 수행하며, 함수 `op`를 적용한 후에 수행됩니다.

!!! compat "Julia 1.11"
    이 함수는 Julia 1.11 이상이 필요합니다.


또한 [`modifyproperty!`](@ref Base.modifyproperty!) 및 [`Core.memoryrefset!`](@ref)를 참조하십시오.
