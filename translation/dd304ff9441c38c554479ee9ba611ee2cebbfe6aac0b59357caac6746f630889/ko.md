```
modifyglobal!(module::Module, name::Symbol, op, x, [order::Symbol=:monotonic]) -> Pair
```

함수를 `op` 적용한 후 전역을 가져오고 설정하는 작업을 원자적으로 수행합니다.

!!! compat "Julia 1.11"
    이 함수는 Julia 1.11 이상이 필요합니다.


또한 [`modifyproperty!`](@ref Base.modifyproperty!) 및 [`setglobal!`](@ref)를 참조하십시오.
