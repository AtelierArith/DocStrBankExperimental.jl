```
swapproperty!(x, f::Symbol, v, order::Symbol=:not_atomic)
```

구문 `@atomic a.b, _ = c, a.b`는 `(c, swapproperty!(a, :b, c, :sequentially_consistent))`를 반환하며, 양쪽 모두에 공통된 `getproperty` 표현식이 있어야 합니다.

또한 [`swapfield!`](@ref Core.swapfield!) 및 [`setproperty!`](@ref Base.setproperty!)를 참조하십시오.
