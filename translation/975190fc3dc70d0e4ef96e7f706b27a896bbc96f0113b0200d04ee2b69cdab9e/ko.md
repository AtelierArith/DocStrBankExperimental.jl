```
setproperty!(value, name::Symbol, x)
setproperty!(value, name::Symbol, x, order::Symbol)
```

구문 `a.b = c`는 `setproperty!(a, :b, c)`를 호출합니다. 구문 `@atomic order a.b = c`는 `setproperty!(a, :b, c, :order)`를 호출하고, 구문 `@atomic a.b = c`는 `setproperty!(a, :b, c, :sequentially_consistent)`를 호출합니다.

!!! compat "Julia 1.8"
    모듈에서의 `setproperty!`는 최소한 Julia 1.8이 필요합니다.


또한 [`setfield!`](@ref Core.setfield!), [`propertynames`](@ref Base.propertynames) 및 [`getproperty`](@ref Base.getproperty)를 참조하십시오.
