```
detect_unbound_args(mod1, mod2...; recursive=false, allowed_undefineds=nothing)
```

유형 매개변수가 바인딩되지 않았을 수 있는 `Method`의 벡터를 반환합니다. 모든 하위 모듈에서 테스트하려면 `recursive=true`를 사용하십시오.

기본적으로 정의되지 않은 기호는 경고를 발생시킵니다. 이 경고는 경고를 건너뛸 수 있는 `GlobalRef`의 컬렉션을 제공하여 억제할 수 있습니다. 예를 들어,

```
allowed_undefineds = Set([GlobalRef(Base, :active_repl),
                          GlobalRef(Base, :active_repl_backend)])
```

는 `Base.active_repl` 및 `Base.active_repl_backend`에 대한 경고를 억제합니다.

!!! compat "Julia 1.8"
    `allowed_undefineds`는 최소한 Julia 1.8이 필요합니다.

