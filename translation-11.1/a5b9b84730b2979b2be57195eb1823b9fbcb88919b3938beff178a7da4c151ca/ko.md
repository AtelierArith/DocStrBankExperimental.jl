```
detect_ambiguities(mod1, mod2...; recursive=false,
                                  ambiguous_bottom=false,
                                  allowed_undefineds=nothing)
```

지정된 모듈에서 정의된 모호한 메서드의 `(Method,Method)` 쌍의 벡터를 반환합니다. 모든 하위 모듈에서 테스트하려면 `recursive=true`를 사용하십시오.

`ambiguous_bottom`은 `Union{}` 타입 매개변수로만 유발된 모호성을 포함할지 여부를 제어합니다. 대부분의 경우 이 값을 `false`로 설정하는 것이 좋습니다. [`Base.isambiguous`](@ref)를 참조하십시오.

`allowed_undefineds`에 대한 설명은 [`Test.detect_unbound_args`](@ref)를 참조하십시오.

!!! compat "Julia 1.8"
    `allowed_undefineds`는 최소한 Julia 1.8이 필요합니다.

