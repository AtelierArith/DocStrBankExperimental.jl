```
Experimental.show_error_hints(io, ex, args...)
```

특정 예외 유형 `typeof(ex)`에 대해 [`Experimental.register_error_hint`](@ref)에서 모든 핸들러를 호출합니다. `args`는 해당 유형의 핸들러에서 예상되는 다른 인수를 포함해야 합니다.

!!! compat "Julia 1.5"
    사용자 정의 오류 힌트는 Julia 1.5부터 사용할 수 있습니다.


!!! warning
    이 인터페이스는 실험적이며 예고 없이 변경되거나 제거될 수 있습니다.

