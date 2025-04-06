```
replaceglobal!(module::Module, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

주어진 값으로 글로벌을 가져오고 조건부로 설정하는 작업을 원자적으로 수행합니다.

!!! compat "Julia 1.11"
    이 함수는 Julia 1.11 이상이 필요합니다.


또한 [`replaceproperty!`](@ref Base.replaceproperty!) 및 [`setglobal!`](@ref)를 참조하십시오.
