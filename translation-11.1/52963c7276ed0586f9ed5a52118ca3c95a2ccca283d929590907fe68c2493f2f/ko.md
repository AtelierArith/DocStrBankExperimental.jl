```
methods(f, [types], [module])
```

`f`에 대한 메서드 테이블을 반환합니다.

`types`가 지정된 경우, 해당 유형과 일치하는 메서드의 배열을 반환합니다. `module`이 지정된 경우, 해당 모듈에 정의된 메서드의 배열을 반환합니다. 모듈 목록도 배열로 지정할 수 있습니다.

!!! compat "Julia 1.4"
    모듈을 지정하려면 최소한 Julia 1.4가 필요합니다.


참고: [`which`](@ref), [`@which`](@ref Main.InteractiveUtils.@which) 및 [`methodswith`](@ref Main.InteractiveUtils.methodswith).
