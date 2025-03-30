```
setpropertyonce!(x, f::Symbol, value, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

`x.f`에 대해 비교 및 교환 작업을 수행하여 이전에 설정되지 않은 경우 `value`로 설정합니다. 함수 호출 형식 대신 `@atomiconce x.f = value` 구문을 사용할 수 있습니다.

또한 [`setfieldonce!`](@ref Core.replacefield!), [`setproperty!`](@ref Base.setproperty!), [`replaceproperty!`](@ref Base.replaceproperty!)를 참조하십시오.

!!! compat "Julia 1.11"
    이 함수는 Julia 1.11 이상이 필요합니다.

