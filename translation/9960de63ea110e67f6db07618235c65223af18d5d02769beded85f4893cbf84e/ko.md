```
Core.set_binding_type!(module::Module, name::Symbol, [type::Type])
```

모듈 `module`에서 바인딩 `name`의 선언된 타입을 `type`으로 설정합니다. 바인딩이 이미 `type`과 동등하지 않은 타입을 가지고 있는 경우 오류가 발생합니다. `type` 인자가 없으면 바인딩 타입이 설정되지 않은 경우 `Any`로 설정하지만, 오류는 발생하지 않습니다.

!!! compat "Julia 1.9"
    이 함수는 Julia 1.9 이상이 필요합니다.

