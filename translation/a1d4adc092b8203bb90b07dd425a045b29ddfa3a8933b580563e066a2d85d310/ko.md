```
Experimental.register_error_hint(handler, exceptiontype)
```

사용자가 오류를 우회할 수 있는 잠재적인 방법을 제안할 수 있는 "힌트" 함수 `handler(io, exception)`를 등록합니다. `handler`는 `exception`을 검사하여 힌트에 적합한 조건이 충족되는지 확인하고, 그렇다면 `io`에 출력을 생성해야 합니다. 패키지는 `__init__` 함수 내에서 `register_error_hint`를 호출해야 합니다.

특정 예외 유형에 대해 `handler`는 추가 인수를 수락해야 합니다:

  * `MethodError`: `handler(io, exc::MethodError, argtypes, kwargs)`를 제공하여 결합된 인수를 위치 인수와 키워드 인수로 분리합니다.

힌트를 발행할 때 출력은 일반적으로 `\n`으로 시작해야 합니다.

사용자 정의 예외 유형을 정의하는 경우, `showerror` 메서드는 [`Experimental.show_error_hints`](@ref)를 호출하여 힌트를 지원할 수 있습니다.

# 예제

```
julia> module Hinter

       only_int(x::Int)      = 1
       any_number(x::Number) = 2

       function __init__()
           Base.Experimental.register_error_hint(MethodError) do io, exc, argtypes, kwargs
               if exc.f == only_int
                    # 색상은 필요하지 않으며, 이는 가능하다는 것을 보여주기 위한 것입니다.
                    print(io, "\nDid you mean to call ")
                    printstyled(io, "`any_number`?", color=:cyan)
               end
           end
       end

       end
```

그런 다음 `Hinter.only_int`를 `Int`가 아닌 것에 호출하면(따라서 `MethodError`를 발생시킴) 힌트를 발행합니다:

```
julia> Hinter.only_int(1.0)
ERROR: MethodError: no method matching only_int(::Float64)
The function `only_int` exists, but no method is defined for this combination of argument types.
Did you mean to call `any_number`?
Closest candidates are:
    ...
```

!!! compat "Julia 1.5"
    사용자 정의 오류 힌트는 Julia 1.5부터 사용할 수 있습니다.


!!! warning
    이 인터페이스는 실험적이며 예고 없이 변경되거나 제거될 수 있습니다. 변경 사항에 대비하기 위해 모든 등록을 `if isdefined(Base.Experimental, :register_error_hint) ... end` 블록 내에 두는 것을 고려하십시오.

