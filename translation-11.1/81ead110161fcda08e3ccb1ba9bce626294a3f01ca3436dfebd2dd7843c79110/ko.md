```
Core.memoryrefswap!(::GenericMemoryRef, value, ordering::Symbol, boundscheck::Bool)
```

원자적으로 `MemoryRef` 값을 동시에 가져오고 설정하는 작업을 수행합니다.

!!! compat "Julia 1.11"
    이 함수는 Julia 1.11 이상이 필요합니다.


또한 [`swapproperty!`](@ref Base.swapproperty!) 및 [`Core.memoryrefset!`](@ref)를 참조하십시오.
