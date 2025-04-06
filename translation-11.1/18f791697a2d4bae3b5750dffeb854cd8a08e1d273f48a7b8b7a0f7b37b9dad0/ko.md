```
replaceproperty!(x, f::Symbol, expected, desired, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

`x.f`의 값을 `expected`에서 `desired`로 교환하는 비교 및 교환 작업을 수행합니다. 함수 호출 형식 대신 `@atomicreplace x.f expected => desired` 구문을 사용할 수 있습니다.

또한 [`replacefield!`](@ref Core.replacefield!), [`setproperty!`](@ref Base.setproperty!), [`setpropertyonce!`](@ref Base.setpropertyonce!)를 참조하십시오.
