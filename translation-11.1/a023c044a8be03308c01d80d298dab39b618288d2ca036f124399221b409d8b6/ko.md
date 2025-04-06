```
swapglobal!(module::Module, name::Symbol, x, [order::Symbol=:monotonic])
```

원자적으로 전역 변수를 동시에 가져오고 설정하는 작업을 수행합니다.

!!! compat "Julia 1.11"
    이 함수는 Julia 1.11 이상이 필요합니다.


또한 [`swapproperty!`](@ref Base.swapproperty!) 및 [`setglobal!`](@ref)를 참조하십시오.
